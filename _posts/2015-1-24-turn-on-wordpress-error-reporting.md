---
title: Turn on WordPress Error Reporting
author: sarathlal
layout: post
tags:
  - WordPress
---

When creating new plugins and themes for WordPress, often we will get blank screen due to errors in our code. In such situations, WordPress have a nice function to help us to debug our code. But in default, WordPress disabled this function to secure our installation.

So now we are going to turn on WordPress error reporting for development and testing session.

First make a copy of `wp-config.php` file from our WordPress installtion folder. We can use this one as a backup to reset wordpress configuration.

Then find out the line that will hide WordPress error reporting in our original file.

	define('WP_DEBUG', false);

First comment out that line and add some additional lines on this file.

	// define('WP_DEBUG', false);

	define('WP_DEBUG', true);
	define('WP_DEBUG_LOG', true);
	define('WP_DEBUG_DISPLAY', false);
	@ini_set('display_errors', 0);

This will generate an error log file (`debug.log`) in `wp-content` folder with detaled error report. We can use this error report to debug our code during development and testing session.

After testing & development, don't forget to remove this settings from `wp-config.php`.
