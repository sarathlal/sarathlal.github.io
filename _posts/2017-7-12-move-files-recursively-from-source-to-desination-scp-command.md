---
title: Move files recursively from source to remote server - SCP Command
layout: post
tags:
  - Linux
  - Linux Commands
---

If we have to move files recursivly from a source directory to remote server, we can use SCP command.

	scp -r source_directory/* user@host:destination_directory

**Example**

	scp -r public_html/* admin@example.com:public_html

The above command will move all files and folders in source machine's `public_html` directory to remote server's `public_html` directory.
