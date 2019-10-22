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

We already can use [Travis-CI](https://travis-ci.org) and [Netlify](https://www.netlify.com) to build and deploy Static Sites, Today we introduce a new way to automate and customize your workflows--GitHub Actions. But we’re just scratching the surface of what GitHub Actions can do. Once you get started, you’ll be able to build, package, release, update, and deploy your project in any language—on GitHub or any external system—without having to run code yourself.

[Sign up for the limited public beta of GitHub Actions](https://github.com/features/actions)

## Step-by-step Instructions

### (1)  Creat a new \<username\>.github.io repository
This's the repository that will contain the fully rendered version of your Hugo website.For [User and Organization Pages sites] (`<username>/<username>.github.io` repository), we have to set `master` branch as our publishing branch.
We should creat a new branch named 'source' to store all markdown codes for blog.

![source branch](https://f000.backblazeb2.com/file/canicula/ImgURL/source+branch.png)

### (2) Add SSH deploy key

Generate your deploy key with the following command.

```sh
ssh-keygen -t rsa -b 4096 -C "$(git config user.email)" -f master -N ""
# You will get 2 files:
#   master.pub (public key)
#   master     (private key)
```
>_note: On Windows, we can use Git Bash, which is the Git command line too._

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

Add your workflow setting YAML file `.github/workflows/main.yml` and push to the `source` branch.
We can refer to the following project, and make some modifications.
#### ⭐️ Repository type - Project

An example workflow for Hugo.

- [peaceiris/actions-hugo: GitHub Actions for Hugo](https://github.com/peaceiris/actions-hugo)

[![peaceiris/actions-hugo - GitHub](https://gh-card.dev/repos/peaceiris/actions-hugo.svg?fullname)](https://github.com/peaceiris/actions-hugo)

![peaceiris/actions-hugo latest version](https://img.shields.io/github/release/peaceiris/actions-hugo.svg?label=peaceiris%2Factions-hugo)
![peaceiris/actions-gh-pages latest version](https://img.shields.io/github/release/peaceiris/actions-gh-pages.svg?label=peaceiris%2Factions-gh-pages)

Add a `.github/workflows/main.yml` file with content like the following:
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
>_note: push on 'source' branch will trigger the workflow,fina/ly publish on 'master' branch._
That's it. See the [action.yml](https://help.github.com/en/github/automating-your-workflow-with-github-actions/workflow-syntax-for-github-actions) file for more information on the available configuration options.

### (4) Build and Deployment
![](https://f000.backblazeb2.com/file/canicula/ImgURL/deploy.png) |

## Summary

At this point, We have everything setup to automatically build and publish your site whenever you push to master. 
Happy blogging!





