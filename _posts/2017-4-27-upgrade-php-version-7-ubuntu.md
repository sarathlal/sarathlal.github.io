---
title:  Upgrade PHP version to 7 on Ubuntu 14.04 / 16.04
layout: post
tags:
  - Ubuntu
  - LAMP
  - PHP
---

### Add PPA

	sudo add-apt-repository ppa:ondrej/php

### Update the Repository

	sudo apt-get update

### Install PHP 7 & necessory modules

	sudo apt-get install php7.0-cli php7.0-common libapache2-mod-php7.0 php7.0 php7.0-mysql php7.0-fpm

	sudo apt-get install mcrypt php7.0-mcrypt php7.0-zip php7.0-soap php7.0-mbstring php7.0-intl php7.0-xml php7.0-curl php7.0-gd

### Disable previous PHP version

	sudo a2dismod php5

### Enable PHP 7

	sudo a2enmod php7.0

### Restart Apache server

	sudo service apache2 restart
