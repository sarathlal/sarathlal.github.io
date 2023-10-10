---
title: Remove last commit from Git repository
layout: post
tags:
  - Git
---

For example, `git log` command gives me the following commit history.

	A -> B -> C -> D [HEAD, ORIGIN]

I need to remove my last commit `D` for local & remote repo like below one.

	A ->B -> C [HEAD,ORIGIN]

## Answer

Step 1: Remove commit from local repo

	git reset HEAD^

Step 2: Forcefully push the new HEAD commit

	git push origin +HEAD

If we want to still have it in our local repo and only remove it from the remote, then we can use below command.

	git push origin +HEAD^:<name-of-our-branch>
