---
title: Track and push empty folders in Git
layout: post
tags:
  - Git
---

My directory structure & files location is like below one.

    parent_dir/sample.txt
    parent_dir/child_dir/abc.txt
    parent_dir/child_dir/xyz.txt

The requirement is that I need to ignore all files in `child_dir`. But I need to include the empty `child_dir` in my source.

There is no direct option to achieve the requirement in `git` because `git` only tracks files and not folders.

The solution is simple. Never empty the directory!

### Solution 1

The `.gitignore` file in root folder is given below.

    parent_dir/child_dir/*.txt

Put this `.gitignore` into the folder. Then add that `.gitignore` file with our source.

    *
    */
    !.gitignore

The file name `gitignore`, makes some confusion in future. So I always prefer the second solution.

### Solution 2

Add an empty file called `.gitkeep` to the folder we want to keep. Modify our .gitignore file like below one.

    # exclude everything
    parent_dir/child_dir/*

    # exception to the rule
    !parent_dir/child_dir/.gitkeep
