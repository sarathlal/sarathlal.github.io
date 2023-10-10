---
title:  Do some action after WooCommerce order completed
layout: post
tags:
  - WordPress
  - WooCommerce
---

If you want to do something after WooCommerce order completed,  we can hook our custom action into `woocommerce_order_status_completed` action hook.

	add_action( 'woocommerce_order_status_completed', 'my_function' );
	/*
	 * Do something after WooCommerce set an order status as completed
	 */
	function my_function($order_id) {
		
		// order object (optional but handy)
		$order = new WC_Order( $order_id );

		// do some stuff here
		
	}
