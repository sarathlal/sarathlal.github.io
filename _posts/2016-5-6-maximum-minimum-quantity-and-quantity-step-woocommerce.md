---
title: Limit maximum, minimum quantity and quantity step - WooCommerce
layout: post
tags:
  - WordPress
  - WooCommerce
---

In WooCommerce product page, there is a quantity field. The user can enter the quantity of items and it will be added to cart.

If you like to limit maximum and minimum quantity a customer can order for a product, use below code snippet. There is also option to control the quantity step.

	add_filter( 'woocommerce_quantity_input_args', 'ef47en_woocommerce_quantity_input_args', 10, 2 );

	function ef47en_woocommerce_quantity_input_args( $args, $product ) {
		$args['input_value']  = 1;    // Starting value
		$args['max_value']      = 100;   // Maximum value
		$args['min_value']      = 1;    // Minimum value
		$args['step']         = 1;    // Quantity steps
		return $args;
	}
