---
title: Move existing, uncommitted changes to a new branch in Git
layout: post
tags:
  - Git
---

When working on the pet projects, regularly I will start some new features and after coding for a bit, I will decide to hold those changes for upcoming releases.

To do so, I need to move the existing uncommitted changes to a new branch and reset my current branch.

Here is the solutions.

### From Git 2.23

Git 2.23 adds the new switch subcommand.

    git switch -c <new-branch>

## Before Git 2.23

    git checkout -b <new-branch>
    git add <files>
    git commit -m "<Brief description of this commit>"
