---
title: 'WooCommerce add to cart button directly redirect to checkout page &#8211; WordPress'
author: sarathlal
layout: post
tags:
  - WooCommerce
  - WordPress
---
In my latest WooCommerce customization, I want to remove cart page in the product purchase flow. That means, when a customer click on the add to cart button, he must go to checkout page directly by skip the Cart page.

This hack is helpful in some specific situations. Lets consider that we are selling E books, Hotel rooms & limited virtual products, this approach may help to increase our sales.

Anyway, just add below code snippet to our theme&#8217;s / child theme&#8217;s `functions.php` file.

	add_filter('add_to_cart_redirect', 'custom_add_to_cart_redirect');
	 
	function custom_add_to_cart_redirect() {
	 global $woocommerce;
	 $checkout_url = $woocommerce->cart->get_checkout_url();
	 return $checkout_url;
	}

Then disable AJAX add to cart button option from Product tab in WooCommerce settings.

Then after reload our product pages & click on add to cart buttons. We can see the magics at there.
