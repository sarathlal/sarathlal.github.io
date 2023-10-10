---
title: Override product short description - WooCommerce
layout: post
tags:
  - WordPress
  - WooCommerce
---

In Default, WooCommerce display our product short description & long description in detail page.

In some customizations, I have to do few modifications like adding a title, adding a wrapper for short description etc. We can use the filter function on such instance.

Here, I'm going to add a title before product short description with the help of filter hook.

	function wpa_a35gy_filter_short_description( $desc ){
		global $product;

		if ( is_single( $product->id ) )
			$new_desc = '<h3>Product Overview</h3>';
			$new_desc .= $desc;
		
		return $new_desc;
	}
	add_filter( 'woocommerce_short_description', 'wpa_a35gy_filter_short_description' );
