---
share: true
title: Tips, snippets & tools
---

### Dataview snippets

To list all pages that are not shared, use this Dataview snippet:

```sql
LIST
WHERE share!=true
```

### CSS snippets

I, as working on my blog, created some cool snippets or useful tools.

#### Grid CSS snippets

> [!info] The snippets is located in [`docs/assets/css/template/utils.css`](https://github.com/ObsidianPublisher/sync_template/blob/main/docs/assets/css/template/utils.css)

Automatically convert the [grid callout layout (from ITS)](https://github.com/SlRvb/Obsidian--ITS-Theme/blob/main/S%20-%20Callouts.css) to mkdocs

![[../assets/img/example_grid_layout.png]]

#### Add a image banner to mkdocs

![image](https://user-images.githubusercontent.com/30244939/163732766-d08b102f-508b-496e-a99f-68f865b2080b.png)

You can add a cool image banner by editing one of your stylesheets and adding:

```css
.md-header {
    background: var(--md-primary-fg-color) url(image_links) left center/cover no-repeat;
}
```

Don't forget to replace `image_link` with the actual link! Personally, I use an image from Unsplash.

## Plugins

### [Mkdocs Callouts](https://pypi.org/project/mkdocs-callouts/)

> [!info] Bundled with the template

> [!info] Plugin's info
> A simple plugin that converts Obsidian-style callouts and turns them into mkdocs-supported Admonitions.
> - <u>Plugin link:</u> <https://pypi.org/project/mkdocs-callouts/>
> - <u>Installation</u>: `pip install mkdocs-callouts`

Use this plugin if you don't want to use the script (either in GitHub Actions or in general). It supports "callouts within callouts" and custom callouts.

### Page encrypted

> [!note] The basic configuration for Material & this template is already included in the `mkdocs.yml` and in `utils.css`

> [!info] Plugin's info
> This plugin allows you to have password-protected articles and pages in MKdocs.
> - <u>Plugin link</u>: <https://pypi.org/project/mkdocs-encryptcontent-plugin/>
> - <u>Installation</u>: `pip install mkdocs-encryptcontent-plugin`

To add a unique page that is encrypted, just add `password: your_secret_password` in your markdown file.

> [!warning] Security
> Obviously, if you use this in a public repository, it is totally useless to add this security (the file can be viewed entirely on GitHub). Do not use this plugin to share sensitive information!

## Custom tags attributes

> [!info] Bundled with the template

> [!info] Custom tags attribute
> Add a [attribute list](https://python-markdown.github.io/extensions/attr_list/) using only hashtags in your text.
> <u>Links</u>: [Custom tags attributes](https://pypi.org/project/mkdocs-custom-tags-attributes/)
> <u>Installation:</u> `pip install mkdocs-custom-tags-attributes`

## Tools

### Modify your notes' metadata in batch

Use [py-obsidianmd](https://selimrbd.github.io/py-obsidianmd/overview/ "py-obsidianmd")

Install:

```python
pip install py-obsidianmd
```

Example:

```python
from pathlib import Path
from pyomd import Notes, Note

path_dir = Path("/path/to/your/directory")
notes = Notes(path_dir)

notes.filter(has_meta=[("tags", "type/book", MetadataType.INLINE)])

notes.metadata.add(k="share", l="true", meta_type=MetadataType.FRONTMATTER)

notes.update_content(inline_inplace=False, inline_position="top", inline_tml="callout") #type: ignore
notes.write()
```