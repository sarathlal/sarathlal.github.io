---
title: Discard local changes in Git
layout: post
tags:
  - Git
---

### Discarding local changes in a file

	git restore file_name

This will undo all uncommitted local changes in the specified file.

#### Example

	git restore index.html

### Discarding all local changes

If we want to undo all of our current changes, we can use the git restore command with the "." parameter.

	git restore .

If we have untracked (new) files in our working copy and want to get rid of those, then use `git clean` command also.

	git clean -f

*Note: Be careful with all these commands! Once we have discarded our local changes, we won't be able to get them back!*

### Discarding all local changes & saving changes on the stash

Sometimes, we won't be sure if we really don't need our local changes anymore. If so, instead of discarding them we can choose to save them temporarily.

	git stash --include-untracked

Running this command will result in a clean working copy. But the changes are saved on Git's `Stash`. So we can restore them at a later point if required.

	git stash pop

The `pop` command will reapply the last saved state. Same time delete and clean it from the Stash.
