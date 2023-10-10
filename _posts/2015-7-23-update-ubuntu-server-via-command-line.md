---
title:  Update Ubuntu server via command line
layout: post
tags:
  - Linux
  - Linux Commands
  - Ubuntu
  - Ubuntu Server
---

When Login in to an Ubuntu server via command line ( using SSH ), we can see an update message with the number of updates available. During server management sessions, regularly I want to update current distro using command line.

To run an update on Ubuntu server, Use below command in terminal.

	sudo apt-get update && sudo apt-get upgrade

If you then re-run this command, you will only be prompted for any further updates if even further (newer) updates have been released.
