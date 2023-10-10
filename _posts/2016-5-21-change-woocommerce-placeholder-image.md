---
title: Customize WooCommerce placeholder image
layout: post
tags:
  - WordPress
  - WooCommerce
---

In WooCommerce, if there is no product image, WooCommerce will display a placeholder image as product image.

To change this placeholder image, use below code snippet.


	add_filter( 'woocommerce_placeholder_img_src', 'psq47_custom_woocommerce_placeholder', 10 );

	/*
	 * Function to return new placeholder image URL.
	*/
	function psq47_custom_woocommerce_placeholder( $image_url ) {
	  $image_url = 'http://wc23.co/wp-content/uploads/2015/08/placeholder.png';  // change this to the URL to your custom placeholder
	  return $image_url;
	}
