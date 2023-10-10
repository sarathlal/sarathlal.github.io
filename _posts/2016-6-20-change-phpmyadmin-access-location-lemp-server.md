---
title: Change phpMyAdmin access location - LEMP server
layout: post
tags:
  - Linux
  - Server
  - LEMP Server

---

If you have a LAMP Server or LEMP Server, every one know that there is a chance for `phpMyAdmin` installation in `http://your_domain_or_IP/phpmyadmin`.

The `/phpmyadmin` is the default access location for `phpMyAdmin` installation.

But we can easily change this one in to custom location like `http://your_domain_or_IP/hidethis` on the LEMP server.

First go the `Nginx` document root directory.

	cd /var/www/html

During the `phpMyAdmin` installation process, the system will create a symbolic link on this location that target to `phpMyAdmin` installation folder.

We can see the details by using `ls` command.

	ls -l

The result will look like,

	total 8
	-rw-r--r-- 1 root root 537 Mar  4 06:46 50x.html
	-rw-r--r-- 1 root root 612 Mar  4 06:46 index.html
	lrwxrwxrwx 1 root root  21 Aug  6 10:50 phpmyadmin -> /usr/share/phpmyadmin

As you can see, we have a symbolic link called `phpmyadmin` in this directory.

To change the accesss location, we have to rename this symbolic link.

	sudo mv phpmyadmin hidethis
	ls -l

The output will look like,

	total 8
	-rw-r--r-- 1 root root 537 Mar  4 06:46 50x.html
	-rw-r--r-- 1 root root 612 Mar  4 06:46 index.html
	lrwxrwxrwx 1 root root  21 Aug  6 10:50 hidethis -> /usr/share/phpmyadmin
	
Just restart Nginx Server.

	sudo service nginx restart

In browser, go to the new address (`http://server_domain_or_IP/hidethis`) and we can see our phpMyadmin Login screen.

Also the default address (`http://server_domain_or_IP/phpmyadmin`) will start to return 404 error page.
