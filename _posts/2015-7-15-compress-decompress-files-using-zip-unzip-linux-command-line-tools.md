---
title:  Compress and decompress files using command line tools - Linux
layout: post
tags:
  - Linux
  - Linux tools
  - Linux Commands
  - Ubuntu
---


In almost default Linux installation, there is no default tools to compress and decompress files. There is utility to archive files called `tar`, but it just archive the files without any compression.

So first we want to install `zip` and `unzip` tools to compress and decompress files.

	apt-get install zip
	apt-get install unzip
	
OR

	sudo apt-get install zip unzip
	
## Compress files / Directory

	zip your_folder *
	
There is no need to add .zip extension or suffix as it is added automatically by `zip` command. Then use the `ls` command to verify new zip file.

	ls
	
To compress an entire directory (including all subdirectories), use -r with zip command and it will recursively compress our files and folders.

	zip -r your_folder *
	
## Decompress files / Directory

	unzip  your_folder.zip
	
To extract one file from compressed directory, we want to specify that file name with extension. 

	unzip your_folder.zip  cv.doc
	
In the above example, I specified the name of the file (cv.doc) to be extracted in unzip command.
	
If we want to extract to a particular destination folder, then we need to specify the destination folder.

	unzip your_folder.zip -d /var/www/

Here I specified the destination folder ( /var/www ) with unzip command.
