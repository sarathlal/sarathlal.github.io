---
title:  Change Place Order button text in WooCommerce checkout page
layout: post
tags:
  - WordPress
  - WooCommerce
---

In one of my recent WooCommerce customization, I want to change `Place Order` button text in checkout page. The WooCommerce have a filter, `woocommerce_order_button_text` and we are going to use this filter to change `Place Order` button text in  Checkout page.

We just want to add below code snippet to our theme's / child theme's `functions.php` file.

	add_filter( 'woocommerce_order_button_text', 'woo_custom_order_button_text' ); 

	function woo_custom_order_button_text() {
		return __( 'Your new button text here', 'woocommerce' ); 
	}
	
That's enough.
