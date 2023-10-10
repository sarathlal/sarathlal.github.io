---
title: Add SKU in cart page detail - WooCommerce
layout: post
tags:
  - WooCommerce
  - WordPress
---

In default, WooCommerce offer minimal information about product on cart page. Often I miss SKU of product on this page & always like to add this unique identifier on these pages.

To add SKU on cart page, we can simply use a filter hook on Item Name.

	add_filter( 'woocommerce_cart_item_name', 'add_sku_in_cart', 20, 3);

	function add_sku_in_cart( $title, $values, $cart_item_key ) {
		$sku = $values['data']->get_sku();
		return $sku ? $title . sprintf(" (SKU: %s)", $sku) : $title;
	}
