---
title: Replace string in multiple files - Command line
layout: post
tags:
  - Linux
  - Linux Commands
---

Go to directory that contain files.

	cd /var/www/posts

Find all PHP files in that folder & replace string `foo` with `bar` in all files.

	find . -name "*.php" -print | xargs sed -i 's/foo/bar/g'
