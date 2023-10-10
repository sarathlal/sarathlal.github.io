---
title:  Automatically shut down computer after downloading files - Linux command
layout: post
tags:
  - Linux
  - Linux Commands
---

To download files, we can simply use `wget` command.

Also to shut down computer we can use `halt` command.

Now to automatically shut down our computer after downloading the files we can use combination of both.

	wget UrlOfTheFileYouWantToDownload && sudo halt

The above commands will only shut down the computer if `wget` returns successfully.

	wget UrlOfTheFileYouWantToDownload ; sudo halt

 This command will run halt whether wget returns successfully or fails.
