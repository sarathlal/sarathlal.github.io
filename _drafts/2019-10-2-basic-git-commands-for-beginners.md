---
title: Basic git commands for beginners
layout: post
tags:
  - git
---

Same like any other developer, the `git` is one of the tool that I'm using regularly 
For version control, `git` is an awesome tool. From the beginning of my coding, I need to use `git`.

So to familiarize with `git` commands, I have created a note with basic commands. These all are essential `git` commands & in my daily development process, I have to use all of them.

If you believe that, I have forgotten to mention about any commands, please share your thoughts with me.

So lets start.

## Know the current status

	git status

This command can return some usefull messages about current status of our repo.

## Initilize init

	git init

Initilize a blank local git repo or an already exisiting repo.

## Stage changes

#### stages all changes

	git add -A

#### stages new files and modifications, without deletions

	git add .

#### stages modifications and deletions, without new files

	git add -u

Note: `git add -A` is equivalent to  `git add .; git add -u`.

## Commit changes

	git commit -m "first commit"

When commit, give a proper title with clue about changes.

## Add a remote origin with local repo

The steps are given below

1. Create a repo in remote service
2. Get repo URL
3. Add remote origin in local repo

Command given below.

	git remote add origin your_remote_repo_url

example:

	git remote add origin https://user@bitbucket.org/user/sample.git

## Push changes to remote host

	git push -u origin

## Manage branches

#### Create new branche

	git checkout -b new-branch

#### Create new branch with existing branch base

	git checkout -b new-branch existing-branch

#### Checkout branch

	git checkout development

#### Merge changes between branches

Merging changes in development branch to master

	git checkout master

	git merge develop

## Tagging

### Add tags

	git tag -a '<tagname>' -m '<tag_message>'

Example 

	git tag -a '1.2.1' -m 'Version 1.2.1 release'

### Push a tag to remote

	git push origin <tagname>

### View all tags

	git tag -l

### Delete tag from local repo

	git tag -d <tagname>

### Delete tag from remote repo

	git push origin --delete <tagname>


## Manage log

To view the log, use below command.

	git log

The `git log` lists the commits made in that repository in reverse chronological order.

If the log is too lengthy, to escape from the screen, you can use `Q` button or `SHIFT` + `Q`.
