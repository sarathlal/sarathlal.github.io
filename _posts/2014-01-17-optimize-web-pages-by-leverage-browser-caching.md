---
title: Optimize web pages by leverage Browser Caching
author: sarathlal
layout: post
tags:
  - APACHE server
  - htaccess
  - Page Optimization
---
The browser caching is a method to optimize web pages by caching some files in users browser and access them instead of accessing it from the web server. The browser caching is a capability of browser.

The leverage browser caching means add some expires or cache control headers in to our web page files to make it updated at different intervals. By adding this different expire headers in web page files, web browsers can store these files on its cache until it is being expired.

Then after, when we hit the corresponding URL, the browser load the cached file from its cache instead of web server.After expiry, when browser need to load this file again, it update the corresponding file from web server with a new expiry header.

##  Important of leverage browser caching

The web pages are not single files. They are set of files including HTML, CSS, scripts, fonts and images etc. When we hit a URL, browser generate separate http request to serve all these files from web server.

When the web server receive lot of request to serve files, its become loaded and by the way it increases load time of web pages in browsers. Also visitors and server may be located in different countries and it make additional latency for file transfer.

In web technology, the CSS file, scripts, fonts and images etc are considered as static resources because there is no chance to occur changes in that files with in short duration. The HTML file is not consider as a static one.

Same time, modern web browser are capable to store files in its cache memory. If so, we force web browser to store these static files in its cache memory with an expire header. When the web browser want to load that URL in between this expiry period, it can utilize cached static files instead of files from web server.

That means we serve these static files locally for web browsers, and it can increase page speed (ie reduced load time) of our web pages.

*   First we want to open `.htaccess`* file in our web folder of Apache web server.
*   Add below lines of code in to `.htaccess` file.
</ul>

		##  EXPIRES CACHING ## 
		<IfModule mod_expires.c>
		ExpiresActive On
		ExpiresByType image/jpg "access 1 year"
		ExpiresByType image/jpeg "access 1 year"
		ExpiresByType image/gif "access 1 year"
		ExpiresByType image/png "access 1 year"
		ExpiresByType text/css "access 1 month"
		ExpiresByType application/pdf "access 1 month"
		ExpiresByType text/x-javascript "access 1 month"
		ExpiresByType application/x-shockwave-flash "access 1 month"
		ExpiresByType image/x-icon "access 1 year"
		ExpiresDefault "access 2 days"
		</IfModule>
		##  EXPIRES CACHING ## 

*   Save .htaccess file.
*   Test the performance and load time of web pages.

In our codes, you can see that we force to add different expiry headers for different files according to their file types. So in between this expiry period, browser serve this cashed files.

###  Notes

*You can access your .htaccess file through cPanel by clicking on the File Manager. When the pop-up box appears, click on the Web Root option and make sure that the &ldquo;Show hidden files&rdquo; option is checked.
