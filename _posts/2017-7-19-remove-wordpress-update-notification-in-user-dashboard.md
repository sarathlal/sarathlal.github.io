---
title:  Remove WordPress update notification on normal user dashboard
layout: post
tags:
  - WordPress
---

In the WordPress dashboard, there is an update notification system is available. It is too helpful for admin users.

If you allow dashboard access for WordPress users like subscribers, he can also see a related update notification. He can't update the core, but he can notify the admin user about the updates.

![WordPress Update Notification in Subscribers dashboard](/images/2017/profile-wordpress-update-notification.png)

It is better to disable core related notification from the normal user dashboard for better security.

	add_action('after_setup_theme','remove_core_updates');
	function remove_core_updates()
	{
		if(! current_user_can('update_core')){
			add_action('init', create_function('$a',"remove_action( 'init', 'wp_version_check' );"),2);
			add_filter('pre_option_update_core','__return_null');
			add_filter('pre_site_transient_update_core','__return_null');
		}
	}
