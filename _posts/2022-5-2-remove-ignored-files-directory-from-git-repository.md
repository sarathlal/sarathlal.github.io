---
title: Remove ignored files / directory from Git repository
layout: post
tags:
  - Git
---

Adding a `.gitignore` file to our repo allows us to specify which files we don’t need to be tracked in our git repo. If we initially added the `.gitignore` file with the file & directory names to be ignored, `git` never track those files & directories. But if the files / directory are already in our git repo, the files / directory will continue there. Now we need to manually delete them from repo.

### Remove files / directory by manually selecting files

    git rm --cached file_1 file_2 dir_1

### Remove files / directory from `.gitignore` file

    git rm --cached `git ls-files -i -c --exclude-from=.gitignore`

The above command lists all files / directory to be excluded as per `.gitignore` file and deletes them.

If the above command does not work, try the following command instead.

    git ls-files -i -c --exclude-from=.gitignore | xargs git rm --cached

This command creates separate rm commands for each file & folder mentioned in `.gitignore` file, using `xargs` command.

Now we have to commit the changes.

    git add .
    git commit -m "Drop files from .gitignore"
    git push

