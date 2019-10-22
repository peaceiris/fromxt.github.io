---
title: Deploying a Hugo Blog with GitHub Actions
description: Recommend some awesome lite website
date: 2019-10-22
categories:
  - "Miscellaneous"
tags:
  - "Miscellaneous"
  - "Hugo"
  - "GitHub Actions"

---

We already can use [Travis-CI](https://travis-ci.org) and [Netlify](https://www.netlify.com) to build and deploy Static Sites, Now a much better way is introduced to deploy automatically using Github Actions which makes it easy to automate all your software workflows, now with world-class CI/CD. Build, test, and deploy our code right from GitHub. Make code reviews, branch management, and issue triaging work the way we want.We can sign up free the beta from [here](https://github.com/features/actions). Let’s dive in.
<!--more-->
## Getting started

### (1)  Creat a new repository named xxx.github.io. 
For [User and Organization Pages sites] (`<username>/<username>.github.io` repository),we have to set `master` branch to `PUBLISH_BRANCH`.
We can creat a new branch named 'source' to store site source codes.
![source branch](https://f000.backblazeb2.com/file/canicula/ImgURL/source+branch.png)

### (2) Add SSH deploy key

Generate your deploy key with the following command.
On Windows, we can use Git Bash, which is the Git command line too

```sh
ssh-keygen -t rsa -b 4096 -C "$(git config user.email)" -f master -N ""
# You will get 2 files:
#   master.pub (public key)
#   master     (private key)
```

Next, Go to **Repository Settings**

- Go to **Deploy Keys** and add your public key with the **Allow write access**
- Go to **Secrets** and add your private key as `ACTIONS_DEPLOY_KEY`

| Add your public key | Success |
|---|---|
| ![](https://f000.backblazeb2.com/file/canicula/ImgURL/deploy-keys-1.jpg) | ![](https://f000.backblazeb2.com/file/canicula/ImgURL/deploy-keys-2.jpg) |

| Add your private key | Success |
|---|---|
| ![](https://f000.backblazeb2.com/file/canicula/ImgURL/secrets-1.jpg) | ![](https://f000.backblazeb2.com/file/canicula/ImgURL/secrets-2.jpg) |

### (3) Create your workflow

Add your workflow setting YAML file `.github/workflows/main.yml` and push to the source branch.
#### ⭐️ Repository type - Project

An example workflow for Hugo.

- [peaceiris/actions-hugo: GitHub Actions for Hugo](https://github.com/peaceiris/actions-hugo)

[![peaceiris/actions-hugo - GitHub](https://gh-card.dev/repos/peaceiris/actions-hugo.svg?fullname)](https://github.com/peaceiris/actions-hugo)

![peaceiris/actions-hugo latest version](https://img.shields.io/github/release/peaceiris/actions-hugo.svg?label=peaceiris%2Factions-hugo)
![peaceiris/actions-gh-pages latest version](https://img.shields.io/github/release/peaceiris/actions-gh-pages.svg?label=peaceiris%2Factions-gh-pages)

We can refer to the project, and make some modifications, as following:

```yaml
name: github pages

on:
  push:
    branches:
    - source

jobs:
  build-deploy:
    runs-on: ubuntu-latest
    steps:
    - uses: actions/checkout@master
      # with:
      #   submodules: true

    - name: Setup Hugo
      uses: peaceiris/actions-hugo@v2.2.2
      with:
        hugo-version: '0.58.3'

    - name: Build
      run: hugo --gc --minify

    - name: Deploy
      uses: peaceiris/actions-gh-pages@v2.5.0
      env:
        ACTIONS_DEPLOY_KEY: ${{ secrets.ACTIONS_DEPLOY_KEY }}
        PUBLISH_BRANCH: master
        PUBLISH_DIR: ./public
```
The above sample is for [Project Pages sites]. (`<username>/<project_name>` repository)

We can get the detail workflow syntax for GitHub Actions from [here](https://help.github.com/en/github/automating-your-workflow-with-github-actions/workflow-syntax-for-github-actions)

On a push on 'source' branche now the blog is built and published.GitHub Pages bulid and deploy log:

![](https://f000.backblazeb2.com/file/canicula/ImgURL/deploy.png) |

## Notes

###  Use the latest and specific release

We recommend you to use the latest and specific release of this action for stable CI/CD.
It is useful to watch this repository (release only) to check the [latest release] of this action.

[latest release]: https://github.com/peaceiris/actions-gh-pages/releases

