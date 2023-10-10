---
title: .htaccess, 404 error and LAMP server
author: sarathlal
layout: post
tags:
  - APACHE server
  - LAMP Server
  - WordPress
---
In my fresh LAMP server, after updating WordPress permalink settings as acustom one, I got 404 error for all pages and posts.

After some searchs and readings, simply I can fix this issue.

First we want to enable the rewrite module in APACHE web server.

    sudo a2enmod rewrite

Then restart the web server to apply the changes:

    sudo service apache2 restart

In WordPress, it utilize .htaccess file to updates its Apache and PHP configuration. That means we are using mod_rewrite in .htaccess files.

If we are using mod_rewrite in .htaccess files, we also want to enable the use of .htaccess files by changing AllowOverride None to AllowOverride All.

For the default website, edit /etc/apache2/sites-available/default.conf or /etc/apache2/sites-available/000-default.conf:

	<Directory var/www/>
	 Options FollowSymLinks
	 AllowOverride All
	</Directory>

After such a change, we want to restart Apache again.

    sudo service apache2 restart
