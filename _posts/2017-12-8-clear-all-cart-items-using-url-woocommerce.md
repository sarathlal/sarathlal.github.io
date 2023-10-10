---
title: Clear all cart items using URL - WooCommerce
layout: post
tags:
  - WordPress
  - WooCommerce
---

In WooCommerce, to remove all cart items, user need to click `remove item` icon one by one in each cart item.

Why we can't add a remove all cart items option in WooCommerce? I think, it is a nice tweak.

Put below code snippet in your theme's `functions.php` or in your custom module's file.

	add_action( 'init', 'woocommerce_clear_cart_url' );
	function woocommerce_clear_cart_url() {
		if ( isset( $_GET['clear-cart'] ) ) {
			global $woocommerce;
			$woocommerce->cart->empty_cart();
		}
	}

Then append `?clear-cart` string in any of our URL & that will clear our whole cart.

	http://ourstore.com?clear-cart
