---
title: Disabling the wp-cron.php - WordPress
layout: post
tags:
  - WordPress
---

Feeling slow performance on your WordPress site? We already know that there is too many reasons like hosting, plugin & theme load etc.

But if you are working on a high traffic WordPress site, one of the reason will be `wp-cron`. This is WordPress's default task scheduler that takes care of things like checking for updates, publishing scheduled posts, and a whole lot of other functions depending on our configurations.

The `wp-cron` runs on every single page load. This means that whether it is needed or not needed, it will run on every page load. The cron is a task on our server and it will definitely take some server resources. 

Also if the site hasn’t been loaded in a while it will have a whole lot of missed tasks to finish up which can greatly compound the loading time.

So now we are going to configure our WordPress site to run our tasks on a regular basis without depending the default `wp-cron`.

1. Open `wp-config.php`

2. add the line on it

		define('DISABLE_WP_CRON', true);

3. Create a system CRON job according to your hosting

		*/5 * * * * wget -q -O - "http://mydomain.com/wp-cron.php" > /dev/null 2>&1

Sometimes it might be required to run PHP directly:

	*/5 * * * * php /home/$USER/public_html/wp-cron.php

You can also do it using curl:

	*/5 * * * * curl -vs -o /dev/null http://mydomain.com/wp-cron.php > /dev/null 2>&1


