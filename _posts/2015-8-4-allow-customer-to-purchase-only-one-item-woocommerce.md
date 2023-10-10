---
title:  Allow customer to purchase only one item - WooCommerce
layout: post
tags:
  - WordPress
  - WooCommerce
---

In one of my recent WooCommerce project, I want to allow user to purchase only one item ( any one, but only one product ) from my shop!

To achive this functionalitty, we want to add a small code snippet in our theme's / child theme's `functions.php` file.

	add_filter( 'woocommerce_add_cart_item_data', 'woo_allow_one_item_only' );

	function woo_allow_one_item_only( $cart_item_data ) {

		global $woocommerce;
		$woocommerce->cart->empty_cart();

		// Do nothing with the data and return
		return $cart_item_data;
		
	}

The above code snippet is a filter function that will work on `woocommerce_add_cart_item_data` filter hook. When we add a new product in to cart, our function become triggered and it will empty current cart items.
