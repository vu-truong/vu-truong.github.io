---
title: Local Folder
---

At the moment, the plugin does not support local folders (or any solution other than GitHub). Local folders can be destructive, and I don't want to risk damaging your Vault with a bad configuration.

So, how can you use a solution other than GitHub? **You can use a private GitHub repository as a bridge between your Vault and your hosted solution**.

1. Configure the plugin to use GitHub as described in the [[Plugin/index|configuration]].
2. Clone the repository on your computer.
3. Add your hosted solution as a remote.
4. You can also use a GitHub Action to **send** your changes to your self-hosted solution. For example:
    - [Copy via SSH (GitHub Actions)](https://github.com/marketplace/actions/copy-via-ssh)
    - [SCP File Transfer](https://github.com/marketplace/actions/scp-file-transfer)
    - [Mirror to Gitlab and running GitLab CI](https://github.com/marketplace/actions/mirror-to-gitlab-and-run-gitlab-ci)
    - [Mirroring Repository](https://github.com/marketplace/actions/mirroring-repository)