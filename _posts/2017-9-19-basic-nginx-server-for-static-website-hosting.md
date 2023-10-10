---
title:  Install & configure a basic nginx server on Debian 8 for static website hosting
layout: post
tags:
  - Managing Server
---

This server configuration is only for static website hosting. No application like PHP, MySql etc. The below configured server only serve HTML, CSS  & javascript files.

### Install Nginx

	sudo apt-get install nginx

### Configure Server

In Nginx server, blocks are the equivalent of Apache’s virtual hosts. So create the server block file `/etc/nginx/sites-available/example.com`.

In this and all following steps, replace `example.com` with our domain name.

#### Create a new configuration file 

	touch /etc/nginx/sites-available/example.com

#### Edit configuration file

	sudo nano /etc/nginx/sites-available/example.com

Update the content

	server {
	listen   80;
	server_name www.example.com example.com;
	access_log /var/www/html/example.com/logs/access.log;
	error_log /var/www/html/example.com/logs/error.log;

	location / {
		root   /var/www/html/example.com/public_html;
		index  index.html index.htm;
	}
	}

#### Create the public_html and log directories referenced above:

	sudo mkdir -p /var/www/html/example.com/{public_html,logs}

#### Enable the site and restart the web server.

	sudo ln -s /etc/nginx/sites-available/example.com /etc/nginx/sites-enabled
	sudo systemctl restart nginx

### To deactivate a site, simply delete the symbolic link and restart Nginx:

	sudo rm /etc/nginx/sites-enabled/example.com
	sudo systemctl restart nginx
