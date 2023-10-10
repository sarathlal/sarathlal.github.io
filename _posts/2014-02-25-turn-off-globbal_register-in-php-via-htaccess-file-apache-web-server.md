---
title: 'Turn off globbal_register in PHP via .htaccess file &#8211; Apache web server'
author: sarathlal
layout: post
tags:
  - htaccess
  - PHP
---
Turning off global_register will prevent PHP from automatically turning any value in the URL into a variable. That’s a good thing because it means that hackers cannot try to insert anything they want into our code simply by inserting it into our URL.

Well written code should be validating the variables anyway, but this provides extra security in case the script does not validate variables properly or if the validation is buggy.

* First we want to open `.htaccess` file*.
* Add below lines in `.htaccess` file.

		register_globals = Off
		display_errors = off

* Then make a new text file and name it as php.ini.
* Copy and paste below code in to that file.

		<IfModule mod_suphp.c>
		suPHP_ConfigPath /home/yourusername
		<Files php.ini>
		order allow,deny
		deny from all
		</Files>
		</IfModule>

This will turn off global_register for your complete public_html folder.

------

If you want to turn off global_register for a add on domain or sub domain folder only, do the above steps in that folder’s `.htaccess` file, make a php.ini file in that folder and replace second line of php.ini file with below code.

	suPHP_ConfigPath /home/yourusername/pubilc_html/yoursubdirectoryname

I tried this method in a Hostgator shared hosting and it works perfectly for me. Ask support from your host provider and then try it yourself.

### Notes

*You can access your `.htaccess` file through cPanel by clicking on the File Manager. When the popup box appears, click on the Web Root option and make sure that the “Show hidden files” option is checked.

