---
title: "[TEMPLATE]: Versioning template and update inputs"
comments: true
date: 2023-06-21
tags: [Template]
description: "Versioning template, cleaning env file and updating inputs for GitHub Actions"
authors:
    - lisandra-dev
categories:
    - Template
---

Hello!

I have made some updates to the GitHub action that accomplish two things:
- Firstly, I added the file `version.txt` to the [sync template](https://github.com/ObsidianPublisher/sync_template), which allows you to know the release number in the release itself.
- I also made edits to certain actions to remove all variables from the `github/.env` file, keeping only the `WORKFLOW_TYPE` key.

## Versioning

The file [`version.txt`](https://github.com/ObsidianPublisher/sync_template/blob/main/version.txt) will be created at the root when the `update` action is run for the first time. Alternatively, you can create it yourself. You need to use the latest [tag number of the template release](https://github.com/ObsidianPublisher/sync_template/releases).

During each run, the action will download the file from the release (named `update.txt`) and compare it with your `version.txt`. If the version in `update.txt` is higher than your version, the release will be downloaded and applied.

## New inputs

Since I removed:
- `GENERATE_GRAPH`
- `AUTO_MERGE`
- `CLEAN`
- `DRY_RUN`

From `.env` file, you need to update your workflow accordingly.

### GENERATE_GRAPH → `deploy.yml`

If you are using `gh-pages`, you **do not need this key**. Otherwise, update your `deploy.yml` as follows:

```yml
jobs:
  deploy:
    uses: ObsidianPublisher/actions/.github/workflows/deploy.yml@main
    with:
      GENERATE_GRAPH: true
```

If you don't intend to use graph generation, do not set this key.

> [!note]
> You need to have the file `requirements-actions.txt` with the following contents:
>
> ```
> obsidiantools==0.10.0
> pyvis==0.3.1
> ```

### AUTO_MERGE → [`update.yml`](https://github.com/ObsidianPublisher/actions/blob/main/template/update.yml)

If you want to automatically update your template files, set the `AUTO_MERGE` input to `true` as follows:

```yaml
jobs:
  update:
    uses: ObsidianPublisher/actions/.github/workflows/update.yml@main
    with:
      AUTO_MERGE: true
```

### CLEAN & DRY_RUN → [`maintenance.yml`](https://github.com/ObsidianPublisher/actions/blob/main/template/maintenance.yml)

- `CLEAN`: Deletes unused images.
- `DRY_RUN`: Logs only.

Update your workflow as follows:

```yaml
jobs:
  maintenance:
    uses: ObsidianPublisher/actions/.github/workflows/maintenance.yml@main
    with:
      CLEAN: true
      DRY_RUN: false
```