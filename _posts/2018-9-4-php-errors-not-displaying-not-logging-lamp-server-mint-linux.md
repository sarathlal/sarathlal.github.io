---
title: PHP Errors not displaying or not logging - LAMP server - Solved
layout: post
tags:
  - LAMP Server
---

I have to set up a new LAMP server in Linux `Mint 19` on yesterday for WP development. 

The configurations are,

1. Apache
2. PHP 7
3. MySQL 5

Later half an hour, I realize that PHP errors are not displaying or not logging.

The issue is due to configuration in PHP configuration file.

Solved it by updating 2 `php.ini` files. The files location are given below. May the file path will different as per our OS, Apache & PHP version.

	/etc/php/7.2/apache2/php.ini 
	/etc/php/7.2/cli/php.ini 

The configurations are given below. We need to find out the line of configuration and update the values. There is chance for multiple lines for same configuration.

	display_errors = On
	track_errors = On
	log_errors = On

Then need to restart Apache.

	sudo service apache2 restart

If still facing issue on error reporting, restart the server.

	reboot
