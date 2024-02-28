---
title: Installation
---

Mkdocs Obsidian is a combination of an Obsidian plugin and a Material mkdocs template that allows you to create a personal wiki site based on your Obsidian Vault.

If you are familiar with GitHub Pages, you can easily use the [Mkdocs Material Template](https://www.squidfunk.github.io/mkdocs-material/) by directly templating it using the [template](https://github.com/ObsidianPublisher/mkdocs-publisher-template/generate).


## Installation steps

To use the Mkdocs Obsidian plugin and create a personal wiki site based on your Obsidian vault, you can follow these steps:

1. Create a GitHub account (if you don't have one already)
2. [Template the blog](https://github.com/ObsidianPublisher/mkdocs-publisher-template/generate) and [follow the steps to configure it](https://obsidian-publisher.netlify.app/template/configuration/#mkdocs-configuration)
4. In parallel, download the Obsidian plugin by using the [BRAT](https://github.com/TfTHacker/obsidian42-brat) or the community plugins panel.
5. Configure the plugin's options by setting the repository name, GitHub username, GitHub token, and branch name.
6. Add the `share: true` key in the frontmatter of the notes you want to publish.
7. Customize the folder options (if desired)
8. Run the commands through the file menu or commands palette.
9. Make sure to allow push access on GitHub.
11. You can deploy your site using GitHub Pages, Netlify, Vercel...

> [!INFO] [[Plugin/Configuration example|See here for advanced configuration within obsidian]]


## Upgrading

To keep your template up to date, you should follow these steps:
1. Add a star to the [ObsidianPublisher/template_overrides](https://github.com/ObsidianPublisher/template_overrides) repository to stay informed about updates.
2. Regularly check for new releases, which will contain:
    - The upgraded files in a `zip` file named `changed_files.zip`
    - All important files (excluding `mkdocs.yml`) in a `zip` file named `release.zip`
    - A list of edited files in the CHANGELOG
3. You can also set up a [Github Actions](https://github.com/features/actions) workflow to automatically update the template files every 24 hours.

Note that, you should not edit or configure the files that are provided with the template.

See [[Actions#Update ()|here]] for more information about the update workflow.