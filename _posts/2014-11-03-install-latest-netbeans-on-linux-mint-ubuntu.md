---
title: Install latest Netbeans on Linux Mint / Ubuntu
author: sarathlal
layout: post
tags:
  - Linux
  - Linux Mint
  - NetBeans
  - Ubuntu
---
We can simply install NetBeans in our Ubuntu or its variants via Software Manager, Synaptic package manager or Advanced Packaging Tool (APT).

But regular updates is missing on package repository and so we only get old versions of software via this methods.

So today, I&#8217;m going to install latest version of NetBeans in my Linux Mint by downloading it from NetBeans website.

1. Download the NetBeans

We can download the latest version of NetBeans from [here][1].

I&#8217;m using NetBeans for PHP development. so now I&#8217;m going to download HTML5 & PHP bundle only.

2. Then go to Downloads folder

		cd Downloads

3. Change the installer file permission to be executable

		sudo chmod +x netbeans-8.0.1-php-linux.sh

4. Execute the installer file

		./netbeans-8.0.1-php-linux.sh

This will start the graphical installer for this package. We can simply complete the installation of NetBeans by follow instructions from this graphical interface.

After the installation, we can start NetBeans from our menu or via command line.

		sudo /usr/local/netbeans-8.0.1/bin/netbeans

 [1]: https://netbeans.org/downloads/index.html
