---
title:  Convert .ppk file to .pem file & connect to remote server via SSH - Linux
layout: post
tags:
  - Linux
  - Linux Commands
  - Ubuntu
  - SSH
---

First install the putty tools, if you don`t have on your Linux installation.

	sudo apt-get install putty-tools

Generate the .pem file from .ppk file with the following command.

	puttygen ppkkey.ppk -O private-openssh -o pemkey.pem

Place the new generated `pemkey.pem` file in your `~/.ssh` directory.

	cp pemkey.pem ~/.ssh

Set the proper permissions for `.pem file`.

	chmod 400 pemkey.pem

To connect via SSH with new `.pem file`, use below command.

	ssh -i pemkey.pem user@server_ip

## To convert .pem file to .ppk file,

	puttygen pemKey.pem -o ppkKey.ppk -O private

`-o` means where to write out the converted putty private key & `-O private` means the output will be in a PuTTY private key format.
