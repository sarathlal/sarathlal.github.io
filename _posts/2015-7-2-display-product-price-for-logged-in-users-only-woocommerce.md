---
title:  Display product price for logged in users only - WooCommerce
layout: post
tags:
  - WordPress
  - WooCommerce
---

In a recent WooCommerce customization, our client ask to hide product price from public. Every one can see the product details. But the price is only visible for logged in users only. We just want to use a simple code snippet in our theme's / child theme's `functions.php` file to achieve this functionality.

	add_filter('woocommerce_get_price_html','members_only_price');
	function members_only_price($price){
	if(is_user_logged_in() ){
		return $price;
	}
	else return '<a href="' .get_permalink(woocommerce_get_page_id('myaccount')). '">Login</a> or <a href="'.site_url('/wp-login.php?action=register&redirect_to=' . get_permalink()).'">Register</a> to view price!';
	}

The above code snippet will show price for logged in users and a link to login / register for not logged in users.
