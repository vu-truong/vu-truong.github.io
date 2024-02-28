---
comments: true
date: 2023-05-22
authors:
    - lisandra-dev
description: "Breaking change on Assets! Optimization of not_found links and preventing too much XHR call."
title: "⚠️ [BREAKING CHANGE] SYNC TEMPLATE v2.0"
categories:
    - Template
---

Hello!
In response to [this issue](https://github.com/ObsidianPublisher/assets/issues/1), I have made updates and modifications to the way "Nonexistent internal links" are verified.

As a result, I have created a new `overrides/hooks` folder, named `on_files`:

```python
import json
import posixpath
import os
from pathlib import PurePosixPath
from mkdocs.structure.files import Files
from mkdocs.config.defaults import MkDocsConfig

def list_existing_pages(config: MkDocsConfig, files: Files):
    pages = []
    output_dir = config['site_dir']
    for file in files:
        if file.is_documentation_page() or file.is_media_file():
            pages.append(file)
    
    with open(posixpath.join(output_dir, 'search', 'all_files.json'), 'w') as f:
        json.dump(pages, f, default=lambda o: o.__dict__, indent=4)

def on_files(files: Files, config: MkDocsConfig):
    if not (posixpath.exists(posixpath.join(config['site_dir'], 'search'))):
        os.mkdir(posixpath.join(config['site_dir'], 'search'))
    list_existing_pages(config, files)
    return files
```

This hook will generate a new `JSON` file called `search_index.json` in the `search` folder.

Why? The existing `search_index.json` file, created by Material Mkdocs, does not include all the files such as root files and images. Hence, it was necessary to create this file directly during the build process.

The file [`url_exists.js`](https://github.com/ObsidianPublisher/assets/blob/main/src/js/url_exist.js) has been updated with the following content:

```js
/**
 * Correct some bug in mkdocs creation for links
 * @param {URL} url 
 * @param {number} typeURL 
 * @returns 
 */
function parseURL(url, typeURL) {

    let ref = "";
    let title = "";
    if (typeURL === 0) {
        ref = url.href;
        title = url.title;
    } else if (type_url === 1) {
        ref = url.src;
        title = url.alt;
    }
    if (ref.match(/index$/)) {
        ref = ref.replace(/index$/, "");
    }
    if (ref.includes("%5C")) {
        ref = ref.replace(/%5C/g, "/");
    }
    if (ref.match(/\.md\/$/)) {
        ref = ref.replace(/\.md\/$/, "/");
    }
    ref = decodeURI(ref);
    if (typeURL === 0) {
        url.href = ref;
        url.title = title;
        if (title.length === 0) {
            title = url.innerText;
            url.title = title;
        }
    } else if (typeURL === 1) {
        url.src = ref;
        url.alt = title;
    }
    return {
        title: title,
        ref: ref,
        url: url
    };
}

/**
 * Use search/all_files.json to check if the url exists
 * @param {URL} url 
 * @param {string} ref
 * @param {string} title
 */
function checkIfInternalLinksExists(ref, title, url) {
    //return if the url is not internal
    //verify by checking if the url starts with the blog url

    fetch("/search/all_files.json")
        .then((response) => response.json())
        .then((json) => {

            let cleanURL = url.href.replace(url.host, "").replace(/http(s)?:(\/){1,3}/gi, "");
            cleanURL = cleanURL.length === 0 ? "./" : cleanURL;
            const test = json.some((doc) => {
                return decodeURI(doc.url) === decodeURI(cleanURL);
            });

            if (!test) {
                console.log(`${decodeURI(cleanURL)} does not exist`)
                const newItem = document.createElement("div");
                newItem.innerHTML = title;
                newItem.classList.add("not_found");
                newItem.setAttribute("href", ref);
                try {
                    url.parentNode.replaceChild(newItem, url);
                }
                catch (error) {
                    console.log(error);
                }
            }
        })
        .catch((error) => {
            console.log(error);
        });
}

var p_search = /\.{2}\//gi;
var ht = document.querySelectorAll("a:not(img)");
for (const anchor of ht) {
    if (
        !anchor.getElementsByTagName("img").length > 0 &&
        !anchor.getElementsByTagName("svg").length > 0 &&
        !anchor.href.includes("#") &&
        anchor.hostname === window.location.hostname
    ) {
        var link = parseURL(anchor, 0);
        checkIfInternalLinksExists(link.ref, link.title, anchor);
    }
}

var p_img = /\.+\\/gi;
var img = document.querySelectorAll("img");
for (const image of img) {
    if (image.hostname === window.location.hostname) {
        var link = parseURL(image, 1);
        checkIfInternalLinksExists(link.ref, link.title, image);
    }
}
```

> [!important] You do not need to modify your JavaScript files if you are using the `cdn` link. The JavaScript file will be automatically updated.
> For more information about using the `cdn`, please refer to the discussion [here](https://github.com/ObsidianPublisher/obsidian-github-publisher/discussions/114).

So, now there is only one `XHR` call, which prevents crashes on large documentation websites. :D

<small>Also, I recently discovered that my work was utilized at CERN, and I couldn't be happier!</small>

> [!warning] You need to update your [`mkdocs.yml`](https://github.com/ObsidianPublisher/sync_template/blob/14d60ec803e2670b0494d2c4cd122446be9517c3/mkdocs.yml#L110) file to include the new hooks:
>
> ```yaml
> hooks:
>  - overrides/hooks/on_page_markdown.py
>  - overrides/hooks/on_env.py
>  - overrides/hooks/on_files.py
> ```