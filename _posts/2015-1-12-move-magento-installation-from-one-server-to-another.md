---
title: Move Magento 1 installation from one server to another
author: sarathlal
layout: post
tags:
  - Magento 1
---

When customizing Magento, after testing on local server, regularly I want to move my Magento installation in to test server and original host with same content.

Also in some special occasions, we want to change our host and domain name for some of this Magento installations.

So making this process as simple, today I’m write down the essential steps to move an installed Magento application.

* Make Magento installation in maintenance mode

Create a new file maintenance.flag in our Magento installation root folder. This file will make our current installation in Maintenance mode and by the way, it prevent user actions on this event.

* Backup files and folders

Either we can use FTP file transfer method or if we have SSH access, we can compress all files & folders as a single file through command line.

* Backup database

If we have SSH access, we can use mysqldump command to backup our Magento database. Else use tools like phpMyAdmin etc to backup database.

* Restore database

Restore database using command line tools or GUI tools like phpMyAdmin etc.

* Edit database tables for new host.

Edit values of web/unsecure/base_url and web/secure/base_url in core_config_data table for our new installation.

	UPDATE core_config_data SET value="http://mynewdomain.com/" WHERE path="web/unsecure/base_url";
	UPDATE core_config_data SET value="https://mynewdomain.com/" WHERE path="web/secure/base_url";

 

* Restore files and folders and edit Magento configuration file.

Restore all files and folders in same file structure in new path. Then edit Magento configuration file (app/etc/local.xml).

	 <host><![CDATA[YOUR_DATABASE_HOSTNAME]]></host>
	 <username><![CDATA[YOUR_DATABASE_USERNAME]]></username>
	 <password><![CDATA[YOUR_DATABASE_PASSWORD]]></password>
	 <dbname><![CDATA[YOUR_DATABASE_NAME]]></dbname>

* Adjust files and folders permission.

All files should have 644 permission and folders should have 755 permission.

* Remove Cache & session files

Just remove all content from var/cache & var/session folders.

* Visit our new domain and our old Magento installation will be there.
