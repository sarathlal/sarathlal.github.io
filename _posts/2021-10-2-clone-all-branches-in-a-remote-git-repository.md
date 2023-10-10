---
title: Clone all branches in a remote Git repository
layout: post
tags:
  - Git
---

One of the remote git repository has master, development & some other branches. I've cloned, pulled, and fetched, but I remain unable to get anything other than the master branch. I need to get all branches from remote.

Here is the solution.

## Bash script

    #!/bin/bash
    for branch in $(git branch --all | grep '^\s*remotes' | egrep --invert-match '(:?HEAD|master)$'); do
        git branch --track "${branch##*/}" "$branch"
    done

## One line command

    git branch -a | grep -v HEAD | perl -ne 'chomp($_); s|^\*?\s*||; if (m|(.+)/(.+)| && not $d{$2}) {print qq(git branch --track $2 $1/$2\n)} else {$d{$_}=1}' | csh -xfs


