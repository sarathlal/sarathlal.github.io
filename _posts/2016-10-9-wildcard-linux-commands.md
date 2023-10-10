---
title: Use wild card in Linux commands
layout: post
tags:
  - Linux
  - Linux Commands
---

A wild card is a character that can be used as a substitute for any of a class of characters in a command. It can increase the flexibility and efficiency of our commands.

### Star Wild card

	ls ab*

The above command will list all file name that start with `ab` like `abc`, `abcd`, `ab3ve`, `ab` etc if they exist.

### Question Mark Wild card

	ls ab?

The above command will list all file name that have three characters in its name & the name must start with `ab` and the last character will be anything like `abc`, `ab3`, `abZ` etc if they exist.

### Square Brackets Wild card

	ls ab[123]

The above command will list files that have name like `ab1`, `ab2` and `ab3` if they exist.

We can also specify a range for this wild card.

	ls ab[a-f]
	
	ls ab[1-9]
	
	ls ab[a-z]
