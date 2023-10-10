---
title:  Move files and folders via command line - Linux
layout: post
tags:
  - Linux
  - Linux tools
  - Linux Commands
  - Ubuntu
---

To move files and folders in Linux via command line, we can use `mv` command. It is very simple and essential one for a Linux user.

	mv ~/Downloads/music.mp3 ~/Music/

In the above example, the music.mp3 is the file to be moved and user's Music folder is the destination folder.

Consider that we have few MP3 files with .mp3 extension in our Download folder and we want to move all of them to Music folder. We can quickly move all of them with a single command, like so:

	mv ~/Downloads/*.mp3 ~/Music/

If you want to moove one file into the parent directory of the current working directory, just enter command like so:

	mv testfile.doc ../
	
The `../` means to move the folder up one level. If we are more inside, like `~/Downloads/today/`, we can still easily move that file with:

	mv testfile.doc ../../

We just want to remember that, each `../` represents one level up. That's all.

