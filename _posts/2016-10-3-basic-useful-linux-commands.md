---
title: Basic & useful Linux commands
layout: post
tags:
  - Linux
  - Linux Commands
---

#### Shuts down the operating system

	halt

#### Shuts down & restarts the operating system

	reboot

#### Clear the terminal

	clear

#### Open the manual page

This command opens the manual page for the command or utility specified.

	man ls

#### Find files or directory

	find / -name grub.conf
	
But this search took several minutes to complete because we have to search all directories and sub directories. So we can specify the directory.

	find /etc -name grub.conf

#### Read the files

	cat grub.conf

#### Read few lines of file

	head /etc/passwd
	
In default, The head command display top 10 lines of a file. But we can specify the number of lines.

	head -n15 /etc/passwd

To display the last bottom lines of file, we have to use tail command.

	tail /etc/passwd
	
Same like head command, we can specify the number of lines.

	tail -n15 /etc/passwd

#### Copy content of a file

	cp file1.txt file2.txt

The `cp` command take the contents of one file and place a copy with the same or different name in the directory of our choice.	

#### Rename file

	mv file1 file2

#### Search term through a file

	grep 'vickey' /etc/passwd

#### Count the word

	wc file1.txt
	
The command output will be in number of lines, number of words and number of character format. If we only need any one of them , use option `-l` for line numbers, `-w` for words and `-c` for characters.

	wc -l file1.txt
	
#### Search and replace words

	sed 's/Windows/Linux/' data.txt > newdata.txt

The above command find the first instance of `Windows` in each line from `data.txt` file and replace that text with `Linux` and save the whole content to `newdata.txt` file.

#### Find the users who currently logged in

	who

#### Displays the environment variables

	env

#### Get the user name of the currently logged-in user

	whoami

#### Display Calender

	cal

The `cal` command will display current month calendar. But we can also specify the year.

	cal 2010

#### Get system date & time

	date

#### Use calculator

	bc
