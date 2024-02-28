---
comments: true
date: 2023-08-12
tags: [Plugin]
description: "Some fix and new features about embedding file."
title: "[PLUGIN] V.6.4.0 : Refactoring, fixing & embedding"
authors:
    - lisandra-dev
categories:
    - Plugin
---


Greetings!

I am delighted to announce the release of the most recent version of Obsidian Publisher (v6.4.0).

This update includes the resolution of various issues and notable enhancements:

- Refinements to the regex match conditions.
- Introduction of rate limits and a verified repository field within the settings. These settings can be updated through the designated button or by utilizing commands. The intention behind these optimizations is to enhance the efficiency of the file-sending process to your repository.
- Implementation of modifications for the rendering of wikilinks and Markdown links. Each wikilink now features an associated "alt" text, and updates have been made to Markdown link alts, aligning them more closely with Obsidian's settings. For instance, when linking to a header, the format will be `[[link#header]] -> [[link#header|link > header]]`. It's worth noting that the exclusion of the BlockID from the alt text is a deliberate choice to prevent potential disruption to the reading experience for users.

Furthermore, I have introduced novel settings for embeds:

- You are now empowered to convert embeds into links via the plugin settings. This involves removing the preceding `!` symbol from embeds. Additionally, edits can be made through the frontmatter; comprehensive instructions are available in the [documentation](https://obsidian-publisher.netlify.app/plugin/settings/per%20files%20settings/).
- A fresh setting has been added, allowing for the addition of characters before embed links. The default option is an arrow (`->`). For instance, `![[file embed]]` will undergo transformation into `-> [[file embed]]`.

I extend my sincere gratitude for your continued support and utilization of Obsidian Publisher!

On a personal note, I'm thrilled to share that it has been over a year since I embarked on the journey of developing this plugin! Through this process, I have gained substantial knowledge in TypeScript, JavaScript, and programming in general. The experience has kindled a deep affection for programming within me, and I owe it all to Obsidian :'D!

The upcoming version will place a significant emphasis on enhancing "strict" and null checking. You can already explore and test these improvements with BRAT :>