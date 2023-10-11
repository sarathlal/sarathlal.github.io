---
title: Migrating code repo from BitBucket to GitHub
layout: post
tags:
  - git
  - GitHub
--- 

Recently, I moved our organization's BitBucket repositories to GitHub for easier use and simpler project management. After exploring different methods, including built-in migration options, and not finding a suitable solution, I used the following commands to complete the migration.

#### Clone the Bitbucket Repository:

    git clone https://user_name@bitbucket.org/workspace_name/repo_name.git

Replace `user_name`, `workspace_name`, and `repo_name` with our Bitbucket credentials and repository information.

#### Change Directory to the Repository:

    cd repo_name/

Now we are in the cloned repository directory.

#### Create Local Tracking Branches:

    git branch -r | grep -v '\->' | sed "s,\x1B\[[0-9;]*[a-zA-Z],,g" | while read remote; do git branch --track "${remote#origin/}" "$remote"; done

This command creates local branches that track remote branches from Bitbucket.

#### Fetch All Remote Branches:

    git fetch --all

This command fetches all remote branches from Bitbucket.

#### Fetch Tags (Forcefully):

    git fetch --tags --force

This command fetches all tags from Bitbucket, forcefully overwriting any existing tags with the same name.

#### Create new repo in GitHub

I manually created all repos one by one in GitHub. There are multiple way to do it in command line like `GitHub CLI` tool etc. Then copy the new remote repo URL.

#### Set New GitHub Repository as Remote:

    git remote set-url origin https://github.com/organization_name/new_repo_name.git

Replace `organization_name` and `new_repo_name` with our GitHub organization and repository information.

#### Checkout and Track Remote Branches (excluding 'master'):

    for remote in `git branch -r | grep -v master `; do git checkout --track $remote ; done

This loop checks out and sets up tracking for all remote branches except 'master'.

#### Push All Local Branches to GitHub:

    git push --all

This command pushes all local branches to our new GitHub repository.

#### Push Tags to GitHub:

    git push --tags

This command pushes all tags to our new GitHub repository.

That's enough.
