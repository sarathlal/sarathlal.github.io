---
title:  Rename files and folders via command line - Linux
layout: post
tags:
  - Linux
  - Linux tools
  - Linux Commands
  - Ubuntu
---

In Linux, there is no special command to rename files and folders. We want to use move command ( `mv` ) to rename files and folders.

If you have to rename one file in the working directory, we can simply use `mv` command.

	mv testfile testfile-2

Now the `testfile` in the working directory will be renamed as `testfile-2`.

If you have to rename files and folders in a different directory ( not in working directory ), we just want to keep the destination folder as same as source folder.

	mv /home/user/Desktop/testfile /home/user/Desktop/testfile-2
	
In the above example, `testfile` in the user Desktop folder will be renamed as `testfile-2`.

There is no complexity at all. If we move a file to the same folder, it will be renamed. That's all.
	
