---
title: Securely copy or transfer files across hosts - command line
layout: post
tags:
  - Linux
  - Server
  - Linux Commands
---

To securely transfer files across hosts, we can use `scp` command. It uses `ssh` protocol for data transfer and provides the same authentication and same level of security as `ssh`.

###  Basic Syntax

	scp user@source:/location/to/file user@destination:/where/to/put

###  Copy files from remote server to local machine

	scp user@remote:/file/to/get /where/to/put

###  Copy files to remote server from local machine

	scp /file/to/send user@remote:/where/to/put
