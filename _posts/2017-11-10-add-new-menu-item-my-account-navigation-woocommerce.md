---
title: Add new menu item in my account navigation - WooCommerce
layout: post
tags:
  - WordPress
  - WooCommerce
---

In a recent WooCommerce project, my client suggest to add a new menu item in the WooCommerce user's `My Account` navigation.

When we add a menu item, we have to also create a new page with some content for that new menu link.

Below you can find the simple code snippet to create a new menu item & page to add content for this new menu item.

	/*
	 * Step 1. Add new menu item to My Account menu - on the 3rd position.
	 */
	add_filter ( 'woocommerce_account_menu_items', 'xrgty37_new_menu_link', 40 );
	function xrgty37_new_menu_link( $menu_links ){
	 
		$menu_links = array_slice( $menu_links, 0, 2, true ) 
		+ array( 'new-menu' => 'New Menu' )
		+ array_slice( $menu_links, 2, NULL, true );
	 
		return $menu_links;
	 
	}
	/*
	 * Step 2. Register Permalink Endpoint
	 */
	add_action( 'init', 'xrgty37_add_endpoint' );
	function xrgty37_add_endpoint() {
	 
		// Check WP_Rewrite
		add_rewrite_endpoint( 'new-menu', EP_PAGES );
	 
	}
	/*
	 * Step 3. Content for the new page in My Account, woocommerce_account_{ENDPOINT NAME}_endpoint
	 */
	add_action( 'woocommerce_account_new-menu_endpoint', 'xrgty37_my_account_endpoint_content' );
	function xrgty37_my_account_endpoint_content() {
	 
		// Content for new page
		echo 'This is content for newly created menu item.';
	 
	}
