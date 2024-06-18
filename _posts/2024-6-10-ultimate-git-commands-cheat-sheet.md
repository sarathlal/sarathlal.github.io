---
title: Ultimate Git Commands Cheat Sheet - Comprehensive Guide for Developers
layout: post
tags:
  - GitHub
  - Git
  - Version control
metadescription: A comprehensive Git cheat sheet covering essential commands for repository management, branching, merging, stashing, remote operations, file permissions, and more, complete with examples.
--- 

Git is an essential tool for version control in software development. This comprehensive Git commands cheat sheet provides detailed information, use cases, and examples to help you manage your repositories effectively.

## Git Configuration

### Set Username and Email
```bash
git config --global user.name "Your Name"
git config --global user.email "your.email@example.com"
```
Sets your username and email address for all repositories on your system.

### Check Configuration
```bash
git config --list
```
Displays the current configuration settings.

## Repository Management

### Initialize a Repository
```bash
git init
```
Initializes a new Git repository or reinitializes an existing one.

### Clone a Repository
```bash
git clone https://github.com/user/repository.git
```
Creates a copy of an existing repository.

## Basic Snapshotting

### Check Status
```bash
git status
```
Displays the state of the working directory and the staging area.

### Add to Staging Area
```bash
git add .
```
Stages all changes (new files, modifications, deletions).

```bash
git add -A
```
Stages all changes in the entire repository.

```bash
git add -u
```
Stages modifications and deletions, without new files.

### Commit Changes
```bash
git commit -m "Commit message"
```
Records the changes to the repository with a descriptive message.

### Remove Files
```bash
git rm filename
```
Removes files from the working directory and staging area.

### Move or Rename Files
```bash
git mv old_filename new_filename
```
Moves or renames files in the repository.

## Branching and Merging

### List Branches
```bash
git branch
```
Lists all local branches in the repository.

### Create a New Branch
```bash
git branch new-branch-name
```
Creates a new branch.

### Create a Branch from an Existing Branch
```bash
git checkout -b new-branch-name existing-branch-name
```
Creates a new branch from the specified existing branch and switches to the new branch.

### Switch Branches
```bash
git checkout branch-name
```
Switches to the specified branch.

### Merge Branches
```bash
git merge branch-name
```
Merges the specified branch into the current branch.

### Delete a Branch
```bash
git branch -d branch-name
```
Deletes the specified branch.

## Remote Repositories

### Add a Remote
```bash
git remote add origin https://github.com/user/repository.git
```
Adds a remote repository.

### View Remotes
```bash
git remote -v
```
Displays the current remotes.

### Fetch from Remote
```bash
git fetch origin
```
Downloads objects and refs from another repository.

### Pull from Remote
```bash
git pull origin main
```
Fetches and integrates changes from the remote repository into the current branch.

### Push to Remote
```bash
git push origin main
```
Uploads local branch commits to the remote repository.

### Update Remote URL
```bash
git remote set-url origin https://github.com/user/new-repository.git
```
Updates the URL of the remote repository.

## Stashing and Cleaning

### Stash Changes
```bash
git stash
```
Stashes the changes in a dirty working directory away.

### Apply Stash
```bash
git stash apply
```
Applies the stashed changes.

### Drop Stash
```bash
git stash drop
```
Removes the latest stash.

### Clean Untracked Files
```bash
git clean -f
```
Removes untracked files from the working directory.

## Reverting Changes

### Discard Uncommitted Changes
```bash
git reset --hard
```
Discards all uncommitted changes in the working directory, returning to the last committed state.

### Revert to a Specific Commit
```bash
git reset --hard commit-id
```
Resets the index and working directory to the specified commit.

## History and Inspection

### View Commit History
```bash
git log
```
Displays the commit history.

### Show a Commit
```bash
git show commit-id
```
Displays the changes introduced by the specified commit.

### View Differences
```bash
git diff
```
Shows changes between the working directory and index.

### Blame a File
```bash
git blame filename
```
Shows what revision and author last modified each line of a file.

## Tagging

### Create a Tag
```bash
git tag -a 1.0 -m "Version 1.0"
```
Creates a new tag.

### Push a tag to remote
```bash
git push origin tag-name
```
### List Tags
```bash
git tag
```
Lists all tags in the repository.

### Push Tags
```bash
git push origin --tags
```
Pushes all tags to the remote repository.

### Delete a Tag
```bash
git tag -d tag-name
```
Deletes the specified tag locally.

### Remove Tag from Remote
```bash
git push origin --delete tag tag-name
```
Deletes the specified tag from the remote repository.

## File Permissions

### Exclude Permission Changes from Git
```bash
git config core.fileMode false
```
Disables tracking of file permission changes.

## Advanced Commands

### Rebase Branch
```bash
git rebase branch-name
```
Reapplies commits on top of another base tip.

### Cherry-pick Commit
```bash
git cherry-pick commit-id
```
Applies the changes introduced by an existing commit.

### Amend Last Commit
```bash
git commit --amend -m "New commit message"
```
Modifies the most recent commit.

### Revert a Commit
```bash
git revert commit-id
```
Creates a new commit that undoes the changes from a previous commit.
