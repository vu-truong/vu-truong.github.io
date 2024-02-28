---
share: true
title: Home
hide:
  - navigation
  - toc
---

Mkdocs Obsidian is a combination of an Obsidian plugin and a Material mkdocs template that allows you to create a personal wiki site based on your Obsidian Vault.
It allows you to publish your notes on GitHub and customize the template to your liking.

<p align="center">
	<a href="https://obsidian.md/"><img src="https://img.shields.io/badge/Auxiliary%20Tool-Obsidian-blueviolet"></img></a><br/>
	<a href='https://ko-fi.com/X8X54ZYAV' target='_blank'><img height='36' style='border:0px;height:36px;' src='https://cdn.ko-fi.com/cdn/kofi1.png?v=3' border='0' alt='Buy Me a Coffee at ko-fi.com' /></a><br/>
</p>

- [Obsidian plugin](https://github.com/ObsidianPublisher/obsidian-github-publisher)
- [Github Discussion](https://github.com/ObsidianPublisher/obsidian-github-publisher/discussions)

## The template support

- [x] Wikilinks (`[[Links]]`)
- [x] File transclusion/embed, both wikilinks and Markdown links
- [x] Obsidian callout and custom callout
- [x] Folder notes and their citation
- [x] Custom attributes
- [x] Sharing state and custom folder hierarchy
- [x] Mobile and desktop compatibility
- [x] File mini preview on hover
- [x] Graph view 🎉 (using [Obsidian Tools](https://github.com/mfarragher/obsidiantools))

---

## Github actions & Obsidian's plugin

### TLDR

1. Install the plugins through Obsidian Community or [BRAT](https://github.com/TfTHacker/obsidian42-brat)
2. Template your blog using the [template](https://obsidian-publisher.netlify.app/template/) and configure it.
3. Configure the plugin options:
    - Repo name
    - Your GitHub username
    - The GitHub token (available [here](https://github.com/settings/tokens/new?scopes=repo))
    - The share key
4. Add the sharing key as `true` in Obsidian's note frontmatter
5. Customize (or not) the folder options
6. Run the commands through the file menu or commands palette.

> [!INFO] For advanced configuration within Obsidian, see [[Configuration example|here]]

---

## Generating the template

1. Click on:[^1][use this template](https://github.com/ObsidianPublisher/mkdocs-publisher-template/generate)
2. Use the name of your choice
3. Follow the instruction [here](https://obsidian-publisher.netlify.app/template/configuration/#mkdocs-configuration)
7. The page will automatically build and published right after!

[^1]: You must be logged in to copy the template. You can also test locally by cloning via HTTPS using the command `git clone https://github.com/ObsidianPublisher/template-gh-pages`, or by downloading the ZIP file from [here](https://github.com/ObsidianPublisher/template-gh-pages/archive/refs/heads/main.zip)
