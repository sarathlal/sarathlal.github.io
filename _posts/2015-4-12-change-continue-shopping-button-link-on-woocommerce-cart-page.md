---
title: Change Continue Shopping button link on WooCommerce cart page
layout: post
tags:
  - WordPress
  - WooCommerce
---

If we set WooCommerce to automatically redirect to the cart when a customer add a product to their cart, a "Continue Shopping" button appears on the cart page.

By default, this "Continue Shopping" button redirects the customer back to the product page that had just been added to the cart.

But If you like to redirect user to WooCommerce Shop page by click on that Continue Shopping button, just use below code snippet in your theme's `functions.php` file.

	<?php
	/**
	 * Return the permalink of the shop page for the continue shopping redirect filter
	 *
	 */
	function my_woocommerce_continue_shopping_redirect( $return_to ) {
		return get_permalink( woocommerce_get_page_id( 'shop' ) );
	}
	add_filter( 'woocommerce_continue_shopping_redirect', 'my_woocommerce_continue_shopping_redirect', 20 );
	?>

Here we use one WordPress function ( `get_permalink()` ) with a WooCommerce function ( `woocommerce_get_page_id()` ) to get Shop page URL from Shop page slug & then return that URL to our custom filter function to modify `woocommerce_continue_shopping_redirect` hook.
