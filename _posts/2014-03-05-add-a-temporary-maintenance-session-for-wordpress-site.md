---
title: Add a temporary maintenance session for WordPress site
author: sarathlal
layout: post
tags:
  - WordPress
---
In some critical situations, we want to shut down our site for a limited time. It may be a maintenance time or any other error resolving session.

In such occasions, adding a maintenance screen & 503 error page is always better option for our visitors.

We can achieve this by adding a simple function in WordPress.

Just add below function in our child theme&rsquo;s `function.php` file.

	<?php
	// Temp Maintenance - with http response 503 (Service Temporarily Unavailable)
	// This will only block users who are NOT an administrator from viewing the website.
	function wp_maintenance_mode(){
		if(!current_user_can('edit_themes') || !is_user_logged_in()){
			wp_die('Maintenance, please come back soon.', 'Maintenance - please come back soon.', array('response' => '503'));
		}
	}
	add_action('get_header', 'wp_maintenance_mode');
	?>

After adding this function, it will add a 503 error page for all users in front end. Same time, we can access back-end & can login as user in back-end. But the administrator can only see front end until we remove this function from our `function.php`.

So after the maintenance session, we want to remove this function to make our WordPress as live again.
