---
title: Create sub directories recursively - Bash script
layout: post
tags:
  - Linux
  - Bash
---

In some situations, I want to create sub directories recursively. It is so simple in Bash. Assume that we have to create directory with name `main`.

	for dir in */; do
	  mkdir "$dir/main"
	done

###  Remove sub directories recursively

	for dir in */; do
	  rm -rf "$dir/main"
	done
