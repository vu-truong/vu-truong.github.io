---
title: Github Configuration
order: "1"
---

![](Github_settings-1.png)

- **Repo name**: The repository where the files will be sent.
- **GitHub username**: Your GitHub username.
- **GitHub Token**:[^1] Get your [GitHub Token here](https://github.com/settings/tokens/new?scopes=repo). The correct settings should already be applied. To avoid generating a new token every few months, select the “No expiration” option. Click the “Generate token” button and copy the token you are presented with on the next page.
- **Branch name**: The branch where the files will be sent. By default, it is set to `main`, but you can change it to whatever you want, as long as the branch exists.
- Automatic branch merging can be disabled.
- You can use the "**test connection**" button to check that all connection parameters are working.

It is possible to use per-file configuration to change the repository name, username, and branch. You can find more information about it [[Per files settings|here]].

## GitHub Workflow

Also, you can configure your GitHub Workflow here :
- You can edit the pull-request "commit" message, allowing to prevent CI or Netlify with `[skip ci]` or `[skip netlify]`. Note that there will be always the PR number appended after the message.
- You can run a GitHub Actions workflow that have a `workflow_dispatch`.

## Configure more than one repository

> [!grid]
> ![[Github_manage_other_1.png]]
> ![[Github_manage_other_2.png]]
> ![[Github_manage_other_3.png]]

You can now manage multiple repository in the settings. It will allows you to use **all** commands on each configured repository. Note that it will use the same conversion settings for all repositories.
Also, token are shared between all repositories.

Each repository can be configured with the settings above (except the token), plus:
- `smartKey` : Aka the `name` of the repository. It will be used to identify the repository in the [[Per files settings]], and in the commands palettes.
- `shareKey` : Allow you to separate the files shared for each repository. Note that if a secondary key is present with the main key, the main repository will be used.
- `Base link` : Only enabled if you use the global [Link building & copy](Plugin.md#Link%20building%20&%20copy).
- `shortcuts` : Allow you to create a shortcut for each repository. The commands will be directly available in the commands palettes. Otherwise, you need to use the `Run command for a repository` command, and choose the repository you want to use. This add more [Per files settings](Per%20files%20settings.md).
- You can also set a copy-links path.

[^1]: A GitHub account and connection is required to create a token.