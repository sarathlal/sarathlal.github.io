---
title: How change the document root of the Apache in LAMP Server?
author: sarathlal
layout: post
tags:
  - APACHE server
  - LAMP Server
  - Linux
  - Linux Mint
---
Basically I want localhost to come from /var/www directory instead of /var/www/html directory in my latest LAMP installation with Linux mint &#8211; 17 OS.

So first find apache configuration file. It may be `default.conf` or `000-default.conf` in /etc/apache2/sites-available.

Then change the root directory from /var/www/html to /var/www and that worked.

Change

    DocumentRoot /var/www/html

in to

    DocumentRoot /var/www

This one works in Latest Apache2 installation on my Linux Mint 17 Cinnamon machine.

But the file to be changed is purely depend with our linux distro & Apache version. So please handle files with care.
