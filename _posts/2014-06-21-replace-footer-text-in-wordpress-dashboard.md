---
title: Replace footer text in WordPress dashboard
author: sarathlal
layout: post
tags:
  - WordPress
---
In WordPress dashboard (control panel), we can see a text in footer that say thanks to us in the use of WordPress. We can replace that text with our own text for better branding.

Just add below code snippet in our child theme&#8217;s functions.php file.

	if (! function_exists('replace_footer_admin') ){
		function replace_footer_admin () {
			echo "Your own text";
		}
	} 

	add_filter('admin_footer_text', 'replace_footer_admin');


In this code snippet, first we create a new function named as `replace_footer_admin` & then we replace default `admin_footer_text` function with this new function using a filter hook.
