---
comments: true
date: 2023-05-27
tags: [Template]
title: "[TEMPLATE]: Reusable workflows"
authors:
    - lisandra-dev
categories:
    - Template
    
---

Hello everyone!

I got tired of checking and updating everything across multiple repositories when working on GitHub action workflows. Using sync was helpful but sometimes tricky, as I wasn't sure what was affecting what.

I spent the whole day searching for a solution to reuse workflows across repositories without having to publish them. And guess what? I found it!

Introducing a new repository: [ObsidianPublisher/actions](https://github.com/ObsidianPublisher/actions). This repository contains all the workflows used to accomplish the following tasks:

- Update the template (from [ObsidianPublisher/sync_template](https://github.com/ObsidianPublisher/sync_template)).
- Deploy to Netlify/Vercel/GitHub Pages (depending on your configuration and whether you want the graph).
- Perform maintenance tasks such as cleaning unused images and updating your `requirements.txt`.
- Create an index.

These new reusable workflows are easier to read and update. Now, I only need to update one repository, and you'll automatically get the latest version. Moreover, you can customize them as per your requirements. For example, you can add specific actions during the deployment process.

