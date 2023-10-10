---
title:  Install LAMP - Apache2 , MariaDB, PHP 7	on Debian 8
layout: post
tags:
  - Debian
  - LAMP
---

Install Apache

	apt-get install apache2

Install MariaDB

	apt-get install mariadb-server

Secure MariaDB installation

	mysql_secure_installation

Add PHP 7 source to debian source list

	nano /etc/apt/sources.list

Add below lines with your other sources

	deb http://packages.dotdeb.org jessie all
	deb-src http://packages.dotdeb.org jessie all

Fetch and install the GnuPG key for new source - Jessie only

	cd /tmp
	wget https://www.dotdeb.org/dotdeb.gpg
	sudo apt-key add dotdeb.gpg
	rm dotdeb.gpg

Insatll PHP 7 & required libraries

	apt-get install php7.0 libapache2-mod-php7.0 libphp7.0-embed php7.0-apcu php7.0-apcu-bc php7.0-bcmath php7.0-bz2 php7.0-cgi php7.0-cli php7.0-common php7.0-curl php7.0-dba php7.0-dbg php7.0-dev php7.0-enchant php7.0-fpm php7.0-gd php7.0-geoip php7.0-gmp php7.0-igbinary php7.0-imagick php7.0-imap php7.0-interbase php7.0-intl php7.0-json php7.0-ldap php7.0-mbstring php7.0-mcrypt php7.0-memcached php7.0-msgpack php7.0-mysql php7.0-odbc php7.0-opcache php7.0-pgsql php7.0-phpdbg php7.0-pspell php7.0-readline php7.0-recode php7.0-redis php7.0-snmp php7.0-soap php7.0-sqlite3 php7.0-ssh2 php7.0-sybase php7.0-tidy php7.0-xdebug php7.0-xml php7.0-xmlrpc php7.0-xsl php7.0-zip

Configure Apache 2 web-server to use PHP 7

	a2enmod proxy_fcgi setenvif
	a2enconf php7.0-fpm

Restart Apache server

	service apache2 restart
