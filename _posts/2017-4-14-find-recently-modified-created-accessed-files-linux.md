---
title:  Find recently modified, created or accessed files - Linux
layout: post
tags:
  - Linux
  - Linux Commands
---

In servers, often I have to find out the recently modified or created files. It is also too helpful to find out source of an attack or infection.

In such situation, we can use `find` tool.

#### List files modified in last 2 hour

	find /directory-to-search -type f -mmin -120

#### List files created in last 2 hours

	find /directory-to-search -type f -cmin -120

#### List files accessed in last 2 hours

	find /directory-to-search -type f -amin -120

#### List files modified in last 1 day

	find /directory-to-search -type f -mtime -1

#### List files created in last 1 day

	find /directory-to-search -type f -ctime -1

#### List files accessed in last 1 day

	find /directory-to-search -type f -atime -1
