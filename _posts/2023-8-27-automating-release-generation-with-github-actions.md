---
title: Automating Release Generation with GitHub Actions
layout: post
tags:
  - GitHub
  - GitHub Actions
  - Automation
--- 

Releasing new versions of software is a critical part of our development workflow. Creating releases manually can be quite a tedious process, but automation can streamline the entire release management process. In this blog post, I'll explain how I automated the creation of release packages using GitHub Actions.

GitHub Actions is a powerful tool that allows me to automate various tasks in my software development workflow. In this example, I've created a GitHub Action that generates a release package in the form of a zip file whenever a new tag is pushed to our repository. The zip file will be named in the format `repo-name-tag-name.zip`. Additionally, I've configured it to exclude specific files from this zip file, and I've achieved this by using a `.gitattributes` file.

## Prerequisites

Before diving into the code, make sure you have the following set up:

1. A GitHub repository for your project.
2. A basic understanding of GitHub Actions.

## Setting up the GitHub Action

The automation is configured through a GitHub Actions workflow file. In my case, the workflow file is named `.github/workflows/release.yml`. Let's break down the code in this workflow file step by step:

```yaml
on:
  push:
    tags:
      - "*"
```

This section defines when the workflow should run. In my case, I've set it up to trigger the workflow on every push to the repository with a tag. The `"*"` wildcard ensures that it runs on any tag.

```yaml
name: Create and Publish release
```

This sets the name of the workflow.

```yaml
jobs:
  build:
    name: Create Release
    runs-on: ubuntu-latest
```

Here, I've defined a job named "Create Release" that runs on the latest version of Ubuntu. This job will execute a series of steps.

### Step 1: Checkout Code

```yaml
- name: Checkout code
  uses: actions/checkout@v2
```

This step checks out the code from the repository.

### Step 2: Get Repo Name and Tag Name

```yaml
- name: Get Repo Name
  id: get_repo_name
  run: |
    repo_fullname="${% raw %}{{ github.repository }}{% endraw %}"
    repo_name="${repo_fullname##*/}"
    echo "REPO_NAME=${repo_name}" >> $GITHUB_ENV
```

```yaml
- name: Get Tag Name
  id: get_tag_name
  run: |
    tag_name="${% raw %}{{ github.ref }}{% endraw %}"
    tag_name="${tag_name#refs/tags/}"
    echo "TAG_NAME=${tag_name}" >> $GITHUB_ENV
```

These two steps extract the repository name and tag name from environment variables and store them in the GitHub Actions environment for later use.

### Step 3: Create Release

```yaml
- name: Create Release
  run: |
    echo "Repository Name: $REPO_NAME"
    echo "Tag Name: $TAG_NAME"
    git archive --format zip --prefix="${REPO_NAME}/" --output "${REPO_NAME}-${TAG_NAME}.zip" HEAD
    echo "REPO_NAME=${REPO_NAME}" >> $GITHUB_ENV
    echo "TAG_NAME=${TAG_NAME}" >> $GITHUB_ENV
```

In this step, I print the repository and tag names to the log. Then, I use the `git archive` command to create a zip file with the specified format and prefix. This zip file will be named after the repository and tag names. The output is stored in the GitHub Actions environment.

### Step 4: Upload Release

```yaml
- name: Upload Release
  uses: softprops/action-gh-release@v1
  with:
    files: "${% raw %}{{ env.REPO_NAME }}-${{ env.TAG_NAME }}{% endraw %}.zip"
```

This step utilizes the `softprops/action-gh-release` action to upload the generated release package (zip file) to the GitHub release page. The file to be uploaded is determined by the `files` parameter, which uses the repository and tag names stored in the environment.

## Excluding Files from the Zip

To exclude specific files from the generated zip file, I can use a `.gitattributes` file. In this file, I specify patterns of files to be excluded. For example:

```plaintext
.* export-ignore
/path/to/excluded-file.txt export-ignore
*.log export-ignore
```

The first line exclude all hidden files & folders from zip archive. The second line tells Git to exclude the `/path/to/excluded-file.txt` and any `.log` files from the zip archive.

## Code

```yaml
on:
  push:
    tags:
      - "*"

name: Create and Publish release

jobs:
  build:
    name: Create Release
    runs-on: ubuntu-latest
    steps:
      - name: Checkout code
        uses: actions/checkout@v2
      
      - name: Get Repo Name
        id: get_repo_name
        run: |
          # Extract repo name from GITHUB_REPOSITORY variable
          repo_fullname="${% raw %}{{ github.repository }}{% endraw %}"
          repo_name="${repo_fullname##*/}"
          echo "REPO_NAME=${repo_name}" >> $GITHUB_ENV

      - name: Get Tag Name
        id: get_tag_name
        run: |
          # Extract tag or branch name from GITHUB_REF
          tag_name="${% raw %}{{ github.ref }}{% endraw %}"
          tag_name="${tag_name#refs/tags/}"
          echo "TAG_NAME=${tag_name}" >> $GITHUB_ENV

      - name: Create Release
        run: |
          echo "Repository Name: $REPO_NAME"
          echo "Tag Name: $TAG_NAME"
          git archive --format zip --prefix="${REPO_NAME}/" --output "${REPO_NAME}-${TAG_NAME}.zip" HEAD
          echo "REPO_NAME=${REPO_NAME}" >> $GITHUB_ENV
          echo "TAG_NAME=${TAG_NAME}" >> $GITHUB_ENV

      - name: Upload Release
        uses: softprops/action-gh-release@v1
        with:
          files: "${% raw %}{{ env.REPO_NAME }}-${{ env.TAG_NAME }}{% endraw %}.zip"
```

By setting up this GitHub Action, I can automate the creation of release packages when new tags are pushed to my repository. This simplifies the release management process and ensures that others can easily access the latest versions of our software. Additionally, by using a `.gitattributes` file, I have fine-grained control over which files are excluded from the release package, providing a more customized release content.
