---
title: Optimize web pages using compression with mod_deflat or mod_gzip Apache modules
author: sarathlal
layout: post
tags:
  - APACHE server
  - htaccess
  - Page Optimization
---
Compression is a simple and effective way to optimize web pages by reducing size of web pages using some algorithms. When we reduce the size of our web pages, it reduce the load time for that web page. It save a lot of bandwidth and serve our web pages quickly. The compression can saves around 50 to 70 percent of the file size.

When we hit a URL from our web browser, our browser send a request to web server to deliver the content in corresponding file. Then the web server check that if the file is available at there. If it is available, web server send a response code (200 K) and then start to send the whole content associated with that file to web browser. This is normally happened in Web.

Just consider that the size of our file in web server is 250KB. When some one hit the URL corresponding to that file, web server understand that the file is available at there, then send response code and start to send the whole file in to his web browser. He want to wait till his web browser receive the whole 250KB file to read that web page.

If we can deliver the same content with a reduced file size of 50KB, the visitor&#8217;s web browser can quickly receive that file than 250KB file. That means, when we reduce the file size, it reduce load time and increase page speed of web pages.

we can reduce the file size of Web pages by compressing it using some modules in web server softwares. This is a major part in web optimization. Through this article, I like to share my knowledge about compression of web content using two modules, mod\_deflate and mod\_gzip in Apache web servers.

##  Top benefits by using compression

1.  A better user-experience, since web pages are load quickly.
2.  SEO benefits, search engines like sites that load faster.
3.  Reduced server load, due to small file size.

##  Why compression is possible in Web environment

We already know that Web pages are almost HTML and CSS files. The CSS and HTML files use a lot of repeated text, whitespace and similar tags. The compression algorithm locates similar strings within a text file and replaces those strings temporarily to make the overall file size smaller.

*   First the browser sends a header telling the server it accepts compressed content. :- `Accept-Encoding: gzip, deflate`
*   Then the server sends a response if the content is actually compressed. :- `Content-Encoding: gzip`
*   Then the browser receives the compressed file which is significantly smaller.
*   If the server doesn&#8217;t send the content-encoding response header, it means the file is not compressed and browser want to receive the uncompressed version.

##  Two Apache modules for compression

The Apache use two modules for compression and decompression.

1.  mod_deflate
2.  mod_gzip

This two modules are based on same deflate algorithm. But the mod\_gzip is little more than mod\_deflate.

We can consider that output of mod\_Gzip have the same output of mod\_deflate with a few dozen byte header wrapped around it including a checksum.

Due to the checksum, mod\_gzip is slower than mod\_deflate in compression and decompression. Also mod\_gzip use little more resource than mod\_deflate due to this checksum.

The mod\_deflate is is easy to configure and well documented. If you are using Apache v2, the mod\_deflate is already installed with Apache. But some old browsers are broken when using mod_deflate.

The compressed file by mod\_gzip is little more than mod\_deflate compressed file due to header and checksum. Additionally some shared and reseller host provider not support mod_gzip.

Any way this two modules are commonly used to compress web content. To utilize any compression, they must be configured and enabled on server. Then we want to add specified codes in our directory level configuration file like `.htaccess`.

##  Enable compression on Apache server using mod_deflate

*   First Open `.htaccess` file in your web server*.
*   Add below lines of code in to your `.htaccess` file.
</ul>

		# compress text, HTML, JavaScript, CSS, and XML
		AddOutputFilterByType DEFLATE text/plain
		AddOutputFilterByType DEFLATE text/html
		AddOutputFilterByType DEFLATE text/xml
		AddOutputFilterByType DEFLATE text/css
		AddOutputFilterByType DEFLATE application/xml
		AddOutputFilterByType DEFLATE application/xhtml+xml
		AddOutputFilterByType DEFLATE application/rss+xml
		AddOutputFilterByType DEFLATE application/javascript
		AddOutputFilterByType DEFLATE application/x-javascript

		# remove browser bugs
		BrowserMatch ^Mozilla/4 gzip-only-text/html
		BrowserMatch ^Mozilla/4\.0[678] no-gzip
		BrowserMatch \bMSIE !no-gzip !gzip-only-text/html
		Header append Vary User-Agent

*   Save `.htaccess` file
*   Test the performance and page size after compression.

##  Enable compression on Apache server using mod_gzip

*   If your host support mod_gzip, add below lines of code in to `.htaccess` file instead of above code snippet.
</ul>

		<ifModule mod_gzip.c>
		mod_gzip_on Yes
		mod_gzip_dechunk Yes
		mod_gzip_item_include file .(html?|txt|css|js|php|pl)$
		mod_gzip_item_include handler ^cgi-script$
		mod_gzip_item_include mime ^text/.*
		mod_gzip_item_include mime ^application/x-javascript.*
		mod_gzip_item_exclude mime ^image/.*
		mod_gzip_item_exclude rspheader ^Content-Encoding:.*gzip.*
		</ifModule>

*   Then save `.htaccess` file and test the performance with page size after compression.

###  Notes

*You can access your .htaccess file through cPanel by clicking on the File Manager. When the popup box appears, click on the Web Root option and make sure that the &ldquo;Show hidden files&rdquo; option is checked.
