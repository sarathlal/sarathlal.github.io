---
title:  Search text in a directory using grep - Linux command line tool
layout: post
tags:
  - Linux
  - Linux tools
  - Linux Commands
---

The `grep` is a powerful command line tool for searching plain-text data sets for lines matching a regular expression. The `grep` was originally developed for the Unix operating system & now it is available for all Unix-like systems.

	grep -rnw 'our_directory' -e "our_search_pattern"

The `grep` command can contain few strings as parameters & that strings can control our searches. In the above example, we have a string `-rnw` & each letters on that string have a specific action.

The `-r` or `-R` is recursive, `-n` is line number and `-w` stands for the whole word. The `-l` (letter L) can be added to get just the file name.

Along with these, `--exclude` or `--include` parameter could be used for efficient searching.

	grep --include=\*.{c,h} -rnw 'our_directory' -e "our_search_pattern"

The above command only search through the files which have `.c` or `.h` extensions.

	grep --exclude=*.c -rnw 'our_directory' -e "our_search_pattern"

The above command will exclude searching all the files ending with `.c` extension.

Same like excluding files, it's possible to exclude/include directories through `--exclude-dir` and `--include-dir` parameter, the following shows how to integrate --exclude-dir:

	grep --exclude-dir={dir1,dir2,*.dst} -rnw 'our_directory' -e "our_search_pattern"

To know more options, use below command to view user manual of grep.

	man grep
