---
date: 2023-03-15
comments: true
description: "Auto update the javascripts & styles.css files using CDN jsdelivr!"
title: "[TEMPLATE]: Using CDN to deliver assets"
authors:
    - lisandra-dev
categories:
    - Template
---

Hello everyone!
Because I needed to keep the repository clean, I had the idea to use an `overrides` HTML file to import CSS and JS linked to the template. After some reflection, and because it was difficult to keep the entire repository updated for the template, I chose to use [jsdelivr](https://www.jsdelivr.com/).

So, the template assets are now in a new `assets` repository ([follow_template](https://github.com/ObsidianPublisher/follow_template)), which will be kept for other files as overrides. A GitHub action will build a new mono-file for JS and CSS.

To use it, you just need to clean up your `mkdocs.yml` and update the `extra_css` and `extra_javascript` as follows:

```yaml
extra_javascript:
  - https://polyfill.io/v3/polyfill.min.js?features=es6
  - https://cdn.jsdelivr.net/npm/mathjax@3/es5/tex-mml-chtml.js
  - https://cdn.jsdelivr.net/gh/ObsidianPublisher/assets@main/dist/javascript.js
extra_css:
    - https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.0.0-beta3/css/all.min.css
    - https://cdn.jsdelivr.net/gh/ObsidianPublisher/assets@main/dist/styles.css
    - assets/css/admonition.css
    - assets/css/custom_attributes.css
    - assets/css/customization.css
```

And that's it :D.