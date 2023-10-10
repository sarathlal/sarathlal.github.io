---
title: Reorder product tabs in single product page - WooCommerce
layout: post
tags:
  - WordPress
  - WooCommerce
---

The default tab order in WooCommerce single product page is given below.

1. Product Description - Post content
2. Additional Information -  Attributes & Values
3. Reviews

![WooCommerce Product Tabs](/images/2017/product-tabs-woocommerce.png)

But in few of our projects, our client asked us to reorder the tab. Below you can find the code snippet that help us to do same. You can use this code snippet in your theme's `functions.php` or in your custom module file.


	add_filter( 'woocommerce_product_tabs', 'woo_reorder_tabs', 98 );
	function woo_reorder_tabs( $tabs ) {

		$tabs['reviews']['priority'] = 5;			// Reviews first
		$tabs['description']['priority'] = 10;			// Description second
		$tabs['additional_information']['priority'] = 15;	// Additional information third

		return $tabs;
	}
