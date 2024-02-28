---
date: 2023-06-21
comments: true
tags: [Plugin]
title: "[PLUGIN]: v6.1.0"
description: "Quickly load preset from a repository & secure your GitHub Token."
authors:
    - lisandra-dev
categories:
    - Plugin
---

The beta cycle has ended!

The update includes two things:
- A method to secure your GitHub token.
- The ability to load presets from a repository.

## GitHub Token

Now, the GitHub Token is stored in an external file, which is saved by default in the plugin folder. The token key is no longer present in the `data.json` file, ensuring that the token is not shared when the file is shared.

By default, this external file is named `env` and can be found in `.obsidian/plugins/obsidian-mkdocs-publisher` (also known as `configDir/plugins/pluginID/env`). You have the option to change this path by clicking the button on the right side of the GitHub token.
![[GitHub Token security & Presets.png]]

The only requirement is that the file must be located within your Obsidian vault. It can be stored in any format, with or without an extension, such as JSON.

The file should be structured as follows:

```env
GITHUB_TOKEN=TOKEN
```

## Presets

Because I believe accessibility is important, I have added a new button: "Load Preset".

This new button allows you to download all files from the `presets` folder in this repository (<https://github.com/ObsidianPublisher/plugin-presets).> You can then choose which settings to load, enabling you to quickly start with the plugin!

### How to add your preset:

1. Fork the project.
1. Add your `data.json` file to the [preset folder](./presets) with a clear and descriptive name.
1. Include documentation in the README.
1. Initiate a Pull Request.

### Presets List:

- [mkdocs.json](https://github.com/ObsidianPublisher/presets/mkdocs.json): Configuration example for [Mkdocs Publisher](https://obsidian-publisher.netlify.app).
