---
title: Disable image Hotlinking via .htaccess
author: sarathlal
layout: post
tags:
  - APACHE server
  - htaccess
---
The Hotlinking is a practice to display image on website by linking to the image on a different server space, rather than keep a copy of that image.

If we hotlinked an image in our web page, When a visitor visit that web page, the image is loaded from another server space & displayed in our web pages.

By the way, we can reduce the total bandwidth of our web server to render our page. But same time we consumed another web server bandwidth to render our page. So hotlinking is normally called as bandwidth theft.

So if you have a website, normally people advise to disable hotlinking from our server because we don&#8217;t have any benefit and unauthorized people utilize our web server bandwidth.

In apache web server, we can easily disable hot linking by adding a few lines in our `.htaccess file`. The `.htaccess file` is our apache configuration file & normally it is a hidden file.

	RewriteEngine On
	RewriteCond %{HTTP_REFERER} !^http://(.+.)?mysite.com/ [NC]
	RewriteCond %{HTTP_REFERER} !^$
	RewriteRule .*.(jpe?g|gif|bmp|png)$ /images/nohotlink.jpg [L]

We just want to replace `mysite.com/` with our own domain in second line & correct image path & name in fourth line.

With this code snippet, first our web server check the referrer to see that it matches our own URL and it is not empty. If it doesn&rsquo;t, and the file has a JPG, GIF, BMP or PNG extension, then the nohotlink image (from forth line of code) is displayed instead.
