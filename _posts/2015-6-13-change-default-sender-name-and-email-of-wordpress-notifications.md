---
title:  Change default sender name and email of WordPress notifications
layout: post
tags:
  - WordPress
---

In default, WordPress use `WordPress@your_website.com` as the sender email and `WordPress` as sender name for all email notifications like forget password, new registrations etc. But in customized WordPress installations, I like to use custom name and email address for all notifications from my application.

So instead of using plugins, I'm going to use a simple code snippet for this WordPress tweaks. So here is a small code snippet to change sender email address and sender name of WordPress notifications.

	add_filter('wp_mail_from', 'new_mail_from');
	add_filter('wp_mail_from_name', 'new_mail_from_name');
	 
	function new_mail_from() {
		return 'yourname@yourdomain.com';
	}
	function new_mail_from_name() {
		return 'Your Name';
	}

We want to add above code snippet in our theme's `functions.php` file and then change the details. That's done.
