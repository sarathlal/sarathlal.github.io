---
title: Check for changes on remote (origin) Git repository
layout: post
tags:
  - Git
---

I have cloned a repository and did some commits to my local repository. In the meantime, my colleagues made commits to the remote repository. Now, I want to know that whether there are any new commits from other people on the remote repository.

Here is the solution.

    git remote update && git status
