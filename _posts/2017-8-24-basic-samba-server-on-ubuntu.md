---
title:  A basic Samba server on Ubuntu
layout: post
tags:
  -  Linux
  -  Server
---

For our development environment, we are recently switched to a common LAMP server on Ubuntu OS.

To access the server space from developer machines, we have to install & configure the Samba suite on the Server.

### Install Samba server

	sudo apt-get install samba

### Configure Samba

Copy default Samba configuartion file as back up

	sudo cp /etc/samba/smb.conf /etc/samba/smb.conf.backup

Edit Samba configuarion file with minumum configuration

	sudo nano /etc/samba/smb.conf

Replace current content with below one

	[global]
	   log file = /var/log/samba-log.%m
	   lock directory = /var/lock/samba
	   share modes = yes

	[homes]
	   comment = Home Directories
	   browseable = no
	   read only = no
	   create mode = 0750


#### Set a psswaord for Samba user

	sudo smbpasswd -a <user_name>

#### Create a home folder for user

	mkdir /home/<user_name>/<folder_name>

#### Restart Samba

	sudo service smbd restart

Now you can use the file explorer window like `\\<your_server_ip>\<user_name>\` in Windows Machine or `smb:\\<your_server_ip>\<user_name>\` in Linux & MAC.
