---
title: Reset a branch to a specific tag in Git
layout: post
tags:
  - Git
---

I have branches named as master and develop. The initial state of master was tagged at `tag_ABC`.

I have a few changes made to the develop branch and pushed to origin. Then accidentally merged develop into master and pushed to origin.

Now I need to revert master to the tag `tag_ABC`.

    git checkout master
    git reset --hard tag_ABC
    git push -f origin master

This will overwrite existing history in the upstream repo and may cause problems for other developers who have this repo checked out.

So other developers who have got master checked out will have to do the following:

    git pull
    git reset --hard origin/master
