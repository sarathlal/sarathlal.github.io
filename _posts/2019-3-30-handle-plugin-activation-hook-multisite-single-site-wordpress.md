---
title: Handle plugin activation hook in multisite & single site - WordPress
layout: post
tags:
  - WordPress
---

Do actions on plugin activation is an important task in all WordPress plugin. If we do some tweaks or save some data in the database during activation, handling plugin activation hook is too important.

If WordPress installation is a single site, we have to do the task in the installed WordPress itself on activation hook. For a multisite, normally we need to do the same task in all network site on activation hook.

Below you can find the code snippet to handle tasks in plugin activation for single site & multisite instance.

	register_activation_hook( __FILE__, '1345_activation_logic' );

	public static function 1345_activation_logic($network_active){
		// If multisite
		if ( function_exists( 'is_multisite' ) && is_multisite() ) {
				// If network activate, iterate through each site
				if ( $network_active ) {
						if ( false == is_super_admin() ) {
								return;
						}

						$blogs = get_sites(); // default count is 100
						foreach ( $blogs as $blog ) {
							$blog_id = $blog->blog_id;
							switch_to_blog( $blog_id );
							do_activation_hook(); // do your activation hook
							restore_current_blog();
						}
				// single site activation in multisite
				} else {
						if ( false == current_user_can( 'activate_plugins' ) ) {
								return;
						}

						do_activation_hook(); // do your activation hook
				}
		// Normal WordPress plugin activation
		} else {
				do_activation_hook(); // do your activation hook
		}
	}


	// Action for creating new site in mulisite setup

	public static function 145561_activate_new_blog($blog_id) {
		if (is_plugin_active_for_network(plugin_basename(__FILE__))) {
			switch_to_blog($blog_id);
			// do action for $blog_id
			restore_current_blog();
		}
	}
	add_action('wpmu_new_blog', '145561_activate_new_blog');

