---
title: User names for connecting to AWS EC2 instances via SSH
layout: post
tags:
  - AWS
---

Recently, I got chance to work with various Linux distributions on Amazon AWS EC2 instances. When creating EC2 instance, normally we will select AMI & AWS done all other tasks.

It never ask for a user name. But when I start to communicate with my server via SSH, the user name is essential.

So here is a small list that show the official AMI SSH user name for various Linux distributions in AWS EC2.

| OS / Distro | User name
| ------------- |:-------------:| 
| Amazon Linux | ec2-user
| Ubuntu | ubuntu
| Debian | admin
| RHEL 6.4 and later | ec2-user
| RHEL 6.3 and earlier | root
| Fedora | ec2-user
| Centos | centos
| SUSE | root
| BitNami | bitnami
| TurnKey | root
| NanoStack | ubuntu
| FreeBSD | ec2-user
| OmniOS | root

Some AMIs are configured like when we start a SSH communication with `root` will output a message informing us the correct user to use and then close the connection. For example,

	$ ssh root@<my_ip>
	Please login as the user "ubuntu" rather than the user "root".
