---
title: Useful bash script for a developer
layout: post
tags:
  - Linux
  - Bash
---

As being a web developer, often I have to do some boring and repeated tasks on files and directories like renaming, removing spaces and replace symbols etc. If we manually do such tasks, it will take long time, effort and it will kill our interest.

In such instance, we can simply use small, one or two line bash scripts to finish the whole jobs in seconds. Below, you can find few bash scripts that useful for developers.

####   script to append a .txt extension to all .log files in a folder

Iterate over the current directory, get all files with .log and append .txt to the end of the entire filename:

	for i in *.log*; do mv "$i" "$i.txt"; done

####   Script to make file names lower case in a folder

Converts all the file names with .txt extension in a directory to lowercase.

	for i in *.txt; do mv "$i" "`echo $i| tr [A-Z] [a-z]`"; done
	
####   Rename all files with a common name and an increment in a folder

Example: Rename all .png files like my_image_1.png, my_image_2.png etc

	j=0;for i in *.png; do echo "my_image_"$j".txt"; j=$(($j+1)); done
	
####   Get all JPG files in a folder and create the appropriate HTML list tags for them and add them to a file

	for i in *.jpg; do echo "<li><img src='images/$i' alt='' /></li>"; done > list_items.html

####   Remove spaces from file names in a folder

	for i in *.html; do mv "$i" "`echo $i| tr -d ' '`"; done
	
####   Replace spaces in file names with underscore symbol in a folder

	for i in *.html; do mv "$i" "`echo $i| tr ' ' '_'`"; done
