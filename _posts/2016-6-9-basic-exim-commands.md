---
title: Basic commands to manage Exim mail server
layout: post
tags:
  - Linux
  - Mail Server
  - Exim
  - Server
---

The Exim is a light weight & highly configurable message transfer agent (MTA) for Unix or Unix-like operating systems with GNU licence.

When I have to manage web server, I like to use Exim for my applications due to the easiness.

We can easily manage `exim` via command line.

* `exim -bp` - shows messages in queue
* `exim -bpc` - shows the no.of messages in queue
* `exim -bP` - shows the current configurations of exim
* `exim -bV` - shows the version and configuration file of exim
* `exiwhat` - Finding out what Exim processes are doing
* `exim -qf` - Force another queue run
* `exim -qff` - Force another queue run and attempt to flush frozen messages
* `exim -Mvl messageID` - View Log for message
* `exim -Mvb messageID` - View Body for message
* `exim -Mvh messageID` - View Header for message
* `exim -Mrm messageID` - Remove message (no errors sent)
* `exim -Mg messageID` - Give up and fail message, message bounces to sender
* `exiqgrep -zi` - List Mail ID (-z : frozen mails only, -i : display message IDs only)
* `exim -M emailID` - Force delivery of one message
