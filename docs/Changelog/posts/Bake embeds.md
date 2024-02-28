---
date: 2023-08-22
categories:
  - Plugin
authors:
  - lisandra-dev
title: "[PLUGIN]: v6.5.0 - Bake embeds"
comments: true
description: Includes the embeds contents in the file, as if the embeds was written directly to the file!
---
Following the [Plugin v6.4.0](Plugin%20v6.4.0.md), and, mainly the new [easy-bake plugin](https://github.com/mgmeyers/obsidian-easy-bake/).  Thanks to [@mgmeyers](https://github.com/mgmeyers/) for this plugin, as I take mostly the code for my version.

So, I added in new settings in `embed` : "include embed contents". This option can be used with `bake` or `include` when using in [per files settings](Per%20files%20settings.md).

The plugin does exactly the same as in easy-bake : the contents of the embed is added in the place of the embed, without markdown or html citation. It supports:
- Block-id
- Heading
- Entire file

> [!info]
> Note that the « embed baking » is done **before** the other text-conversion, including regex. Also, normally, it should recognize the `share` and other sharing key for repository.
> For the file not shared, the links are keep as it was.

The plugin is, for the moment, in beta.

> [!important]
> If you enjoy this function, please, support [@mgmeyers](https://github.com/sponsors/mgmeyers)