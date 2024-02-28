---
date: 2023-05-26
comments: true
description: "Optimization of the graph's generation, using a new action called changed-files. The graph won't be generated if no new files and renamed files are found."
title: "[SYNC TEMPLATE v.2.0]: Optimization of graph's generation (Advanced Workflow)"
authors:
    - lisandra-dev
categories:
    - Template
---

In [[advanced]], I have created a tutorial on a GitHub Action that allows generating graphs without breaking the Netlify/Vercel build. The graph is generated **prior to** the build and it is always generated, even if no new markdown files are created.

To optimize the process and avoid wasting time, I have modified the workflow to include `tj-actions/changed-files@v36`. This action checks if any file in `docs/**/**.md` is new or has been renamed. 
If a new or renamed file is detected, the Python build will be triggered, and the graph will be generated.
If no changes are found, the action will be ignored, and the build will proceed as usual.

Please make sure to update your [`advanced_deploy.yml`](https://github.com/ObsidianPublisher/sync_template/blob/main/.github/workflows/advanced_deploy.yml) file if you are using this specific workflow!