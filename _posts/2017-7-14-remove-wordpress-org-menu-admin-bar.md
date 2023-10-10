---
title:  Remove WordPress.org menu from toolbar
layout: post
tags:
  - WordPress
---

![WordPress.org menu in toolbar](/images/2017/wordpress-org-menu-toolbar.png)

	/*Remove WordPress.org menu from toolbar*/
	add_action( 'admin_bar_menu', 'remove_wp_logo', 999 );
	function remove_wp_logo( $wp_admin_bar ) {
		$wp_admin_bar->remove_node( 'wp-logo' );
	}
