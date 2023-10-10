---
title: Change the directory name of Git repository
layout: post
tags:
  - Git
---

I have some projects as a git repo. Some times, I need to change the directory names of my project. Normally directory name changes are not considered as a chnage in `git`. Also I have some CI / CD code related with repo names.

I always use remote repos. Now consider that all our changes are already committed & pushed to the remote branch. If so, the workflow is given below.

Step 1. Clone the repo in to a different destination

    git clone <repo-url> <new-directory-name>

Step 2. Create a new repo in a remote server with a new name. Note down the new repo URL.

Step 3. Navigate to cloned repo

    cd <new-directory-name>

Step 4. Set new origin URL

    git remote set-url origin <new-repo-url>

Step 5. If you have to do any changes, do the changes, commit & push. Else just push to the remote using the push command.
