---
title:  A quick guide to write your first Bash script
layout: post
tags:
  - Linux
  - Bash
---

As a developer, I want to regularly use commands on terminal in my Linux machine.  But if we want to repeat multiple commands, one after the another, then we can simply use shell scripts with bash.

With a bash script, we can stack up commands, store them in a file, and run the stack of commands by executing this newly created bash script.

This is my first quick guide about Bash scripting and on this post, we are going to create a simple bash script to print out a "Hello, World".

## Create the script

	sudo nano hello.sh

We are opened a file `hello.sh` on current working directory. This is same like creating a new file because if there is no such a file, the above command will create a new file with same name.

Please note that the extension of this newly created file is `.sh`. That means this newly created file is a shell script.

Else just create a new file with `.sh` extension and open it.

## Define which interpreter to use

On the first line of this file, we want to define which interpreter to use for this script. Now we are going to use bash and we want to define it.

	#!/bin/bash  
	
##  Write our program

On the second line of this script, we are writing our program to echo a "Hello, World".

	echo "Hello, World"

##  Save the file.

We just completed our first shell script & we want to save the script. The content on saved script will look like below one.

	#!/bin/bash 
	echo "Hello, World"

## Give executable permission to this file

We want to run this newly created shell script. So we want to give executable permission for this file.

	chmod a+x hello.sh   #Gives everyone execute permissions

or

	chmod 700 hello.sh   #Gives read,write,execute permissions to the Owner
	
## Run the script

Now open a terminal and run the script like this:

	sudo ./hello.sh
	
## Result

The above command will print a "Hello, Word" in the terminal.

	Hello, Word
