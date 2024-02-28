---
title: Customization
---

> [!warning] Don't edit any files in the `assets/css/template` folder! These file will be overwrite when updated.

## Custom and tags attributes

### Tags

The plugin [Custom tags attributes](https://pypi.org/project/mkdocs-custom-tags-attributes/) will convert all `#tags` to `**#tags**{: #tags .hash}` and add custom CSS to it.

> [!example] `2022/01/01` will become `**#2022/01/01**{: #2022/01 .hash}` : #2022/01/01

### Inline Markdown attributes

You can create [Inline Markdown Attributes](https://python-markdown.github.io/extensions/attr_list/) using hashtags. For example, to align some text to the right:
1. 1. Add the following CSS to your `assets/css/custom_attributes.css`:

```css
#right {
 display: inline-block;
 width: 100%;
 text-align: right;
 font-weight: normal;
}

#blue {
  color: blue;
}
```

1. 2. Add `#right` at the end of the line you want to align to the right, and `#blue` on a random word.

```md
Lorem ipsum dolor sit amet, consectetur adipiscing#blue elit. In mollis, libero porttitor gravida accumsan, justo metus pulvinar nulla, vitae dictum odio ligula non nisl. Vivamus id venenatis nulla. Nullam sed euismod ligula. Pellentesque tempor elit felis, lobortis vulputate risus gravida et. Curabitur auctor sed libero nec consectetur. Nam placerat rhoncus risus, euismod sagittis eros bibendum ac. Maecenas tellus libero, porttitor ac purus sit amet, viverra suscipit dolor. Proin id nisl velit. Ut at tincidunt libero, ac pharetra mi. Integer non luctus nisi.#right
```

It will appear as:

Lorem ipsum dolor sit amet, consectetur adipiscing#blue elit. In mollis, libero porttitor gravida accumsan, justo metus pulvinar nulla, vitae dictum odio ligula non nisl. Vivamus id venenatis nulla. Nullam sed euismod ligula. Pellentesque tempor elit felis, lobortis vulputate risus gravida et. Curabitur auctor sed libero nec consectetur. Nam placerat rhoncus risus, euismod sagittis eros bibendum ac. Maecenas tellus libero, porttitor ac purus sit amet, viverra suscipit dolor. Proin id nisl velit. Ut at tincidunt libero, ac pharetra mi. Integer non luctus nisi.#right

Note that there may be some strange behavior caused by the functionality of the [attribute list](https://python-markdown.github.io/extensions/attr_list/) extension, but it generally works well for the majority of use cases.

You can find more information in the [mkdocs-custom-tags-attributes](https://pypi.org/project/mkdocs-custom-tags-attributes/) documentation.

## Folder note

You can create a folder note if you use a `category` front matter key that has the last folder with the same name as the file. See [[Upload#Folder note|Folder note]] for more information.

> [!example] For example,
> `category: folder1/folder2/filename`
> `filename: filename`
> The file `filename` will be renamed to `index`[^1] and the folder will be named `filename`.
> The folder note creation is also supported if you don't use a front matter key to rename the file.

Folder note is also supported by the Obsidian Path, and you can use the [alx-folder-note plugin](https://github.com/aidenlx/alx-folder-note) to help you. [[Plugin/index]] will support both inside and outside methods, alongside the `index` methods.

> [!warning] Folder note is not supported in the `fixed folder` methods.

## Callout & Admonition

The script supports custom admonitions. To do this, you first need to edit or create a new CSS file, adding support for the new custom callout as described in the [Admonition's documentation](https://squidfunk.github.io/mkdocs-material/reference/admonitions/#customization).
For example, to add a `dictionary` admonition:

```css
:root {
    --md-admonition-icon--dictionary: url('data:image/svg+xml;charset=utf-8, <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24"><path d="M18 22a2 2 0 0 0 2-2V4a2 2 0 0 0-2-2h-6v7L9.5 7.5 7 9V2H6a2 2 0 0 0-2 2v16a2 2 0 0 0 2 2h12z"/></svg>')
}
.md-typeset .admonition.dictionary,
.md-typeset details.dictionary {
  border-color: rgb(43, 155, 70);
}
.md-typeset .dictionary > .admonition-title,
.md-typeset .dictionary > .summary {
  background-color: rgba(43, 155, 70, 0.1);
  border-color: rgb(43, 155, 70);
}
.md-typeset .dictionary > .admonition-title::before,
.md-typeset .dictionary > summary::before {
  background-color: rgb(43, 155, 70);
  -webkit-mask-image: var(--md-admonition-icon--dictionnary);
          mask-image: var(--md-admonition-icon--dictionnary);
}
```

It will give you :

> [!dictionnary] Dictionary
> Here's a callout block.
>  It supports **markdown** and `[[wikilinks]]`

The `dictionary` will be recognized, and converted!

## Article list

![[Article_list.png]]
A new, cool way to display your article or post is to use a special template.

To organize that, you must use:

- Pagination indexes
- An `index.md` file in a folder (a "category" folder).

This `index` is in this form:

```md
---
template: blog.html
title: Folder Index
category: FolderName
hidden: True
---
A cool description
```

You need :
- The [`overrides/article.html`](https://github.com/ObsidianPublisher/sync_template/blob/main/overrides/article.html) template
- The [`overrides/partials/post-list.html`](https://github.com/ObsidianPublisher/sync_template/blob/main/overrides/partials/post-list.html) file.

If you want to hide a file from this list, you can use the `hidden` key in the frontmatter.

> [!Warning] Plugin
> The displayed dates relies on a plugin named [`mkdocs-git-revision-date-localized-plugin`](https://github.com/timvink/mkdocs-git-revision-date-localized-plugin). Don't forget to customize it!

> [!warning] To add a illustrative image, you need to add a frontmatter in the file.
> 1. Internal Image : `image:`
> 		This image must be the image name (+ extension) and placed in `assets/img`
> 1. External image: `banner:`

Finally, it's possible to configure the display of the page number (pagination) and the translation with modifying the `extra` key in the mkdocs configuration file [`mkdocs.yml`](https://github.com/ObsidianPublisher/sync_template/blob/main/mkdocs.yml#L135).

> [!note] You can also use the github action `create_index` to create a new index for a new folder.
> For more information see [[Actions]].

## Comments

In `overrides/partials`, you will spot a file named `comments.html`. This allows you to set up comments on your blog! It uses [Giscus](https://giscus.app) to set up this.

First, follow the tutorial on [Material Mkdocs](https://squidfunk.github.io/mkdocs-material/setup/adding-a-comment-system/). After, copy-paste the script of Giscus, as :

```html
<script
  src="https://giscus.app/client.js"
  data-repo="<username>/<repository>"
  data-repo-id="..."
  data-category="..."
  data-category-id="..."
  data-mapping="pathname"
  data-reactions-enabled="1"
  data-emit-metadata="1"
  data-theme="dark-dimmed"
  data-lang="fr"
  crossorigin="anonymous"
  async
>
</script>
```

> [!note] For the theme, you can put `dark-dimmed`.

You need to put this text into the [`overrides/partials/comments.html`](https://github.com/ObsidianPublisher/sync_template/blob/main/overrides/partials/comments.html) file, right after the `<h2>` part.

You can disable or enable comments on a specific page by adding `comments: false` in the frontmatter, and disable/enable globally using the same key in `extra` of `mkdocs.yml` ([here](https://github.com/ObsidianPublisher/sync_template/blob/main/mkdocs.yml#L132)).

- If you disable globally with `comments: false`, you can **enable** it on a specific page by adding `comments: true` in the frontmatter.
- Otherwise, if you enable globally with `comments: true`, you can **disable** it on a specific page by adding `comments: false` in the frontmatter.

> [!warning] You need the last version of the [`overrides/hooks/on_env.py`](https://github.com/ObsidianPublisher/sync_template/blob/main/overrides/hooks/on_env.py) file.

> [!info] It's also possible to use [chirpy](https://chirpy.dev/). The extra_javascript contains already all JS to personalize the comments.
> [You will found a tutorial here](https://github.com/ObsidianPublisher/obsidian-github-publisher/discussions/44).

## Graph view

> [!important] If you won't add a graph view, you need to edit your [`mkdocs.yml`](https://github.com/ObsidianPublisher/template-gh-pages/blob/main/mkdocs.yml#L139) file and **set** the key `generate_graph` to `false`.
> By default, the graph will be generated.

I succeeded to create a semi-interactive graph-view using python. It doesn't allow you to click on article/post, but you can see a view of your blog.

> [!note] Notes
> [obsidiantools](https://github.com/mfarragher/obsidiantools) support actually only 3.9. If you use Netlify to build your blog, you will be forced to use an older version because Netlify only support 3.8. These version won't be perfect.
> I successfully found a way to use graph on Netlify (and Vercel). Check it [[advanced_workflow|here]]!

To use it, you need to install `obsidiantools` and `pyvis` (for the graph view).

```bash
pip install obsidiantools
pip install pyvis
```

(Don't forget to add it to `requirements.txt`)

If you don't have it, you need to download the last version of these files :
- [`overrides/hooks/on_env.py`](https://github.com/ObsidianPublisher/sync_template/blob/main/overrides/hooks/on_env.py)

And create a new file `graph.md` in `docs/` with this content :

```md
<iframe id="test"
        title='test'
        src="../assets/graph.html"
        class="graph"
        width="750px"
        height="750px"
        allowtransparency="true"
        style="border: 0px; margin: 0px; padding: 0px; overflow: hidden;"
        scrolling="no">
</iframe>
```

> [!note] By default, the file will be generated in `docs/assets`. I advise you to exclude this file from git by adding its path to your `.gitignore` file.

![TADA](https://user-images.githubusercontent.com/30244939/205411586-ced48127-908c-45a6-b02f-9d3cb85cc8f6.png)

> [!warning] About creating a graph for each file
> I don't think it's a good idea because :
> - The number of generated file will be huge.
> - The build time will explode.

[^1]: You can use the settings to use another name, but remember that only `index` is supported by Mkdocs.