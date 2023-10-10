---
title:  Check if product is already in cart and use custom Add to Cart button text - WooCommerce
layout: post
tags:
  - WordPress
  - WooCommerce
---

If one a product is already in user cart, displaying a different text instead of default `Add to Cart` text for `Add to Cart` button is a nice idea for E-Commerce  stores.

In one of my WooCommerce customization, I need this tweak. It is too simple in WooCommerce because WooCommerce have exact filter hook to change this add to cart button text.

Before changing `Add to Cart` button text, we want to check if the item is already in user cart. Then according to the status of the item, we want to return the text for the `Add to Cart` button.

	/**
	 * Change the add to cart text on single product pages
	 */
	add_filter('single_add_to_cart_text', 'woo_custom_cart_button_text');

	function woo_custom_cart_button_text() {

	  global $woocommerce;
		
		foreach($woocommerce->cart->get_cart() as $cart_item_key => $values ) {
			$_product = $values['data'];
		
			if( get_the_ID() == $_product->id ) {
				return __('Already in cart - Add Again?', 'woocommerce');
			}
		}
		
		return __('Add to cart', 'woocommerce');
	}

	/**
	 * Change the add to cart text on product archives
	 */
	add_filter( 'add_to_cart_text', 'woo_archive_custom_cart_button_text' );

	function woo_archive_custom_cart_button_text() {

		global $woocommerce;
		
		foreach($woocommerce->cart->get_cart() as $cart_item_key => $values ) {
			$_product = $values['data'];
		
			if( get_the_ID() == $_product->id ) {
				return __('Already in cart', 'woocommerce');
			}
		}
		
		return __('Add to cart', 'woocommerce');
	}
