---
title: Get all variations of a variable product - WooCommerce
layout: post
tags:
  - WooCommerce
  - WordPress
tested: WordPress 5.3.2, WooCommerce 3.9.2
---

To get all variations ID of a variable product, we can use the below code snippet.

	$product = wc_get_product($product_id);
	$variations = $product->get_available_variations();
    $variations_id = wp_list_pluck( $variations, 'variation_id' );

The above code will provide visible variation IDs only. For example, If the price is not set for a variation, that variation will be hidden.

Altrenativly we can use the below code snippet to get all variations without considering visibility.

	$product = wc_get_product($product_id);
	$current_products = $product->get_children();
