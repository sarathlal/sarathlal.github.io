---
title: Move Pagination to top - WooCommerce
layout: post
tags:
  - WordPress
  - WooCommerce
---

In Default, WooCommerce display a nice pagination on the bottom of shop and archive pages.

If you plan to display this pagination on the top of the pages, use below code snippet.

	/* Show pagination on the top of shop page */
	add_action( 'woocommerce_before_shop_loop', 'woocommerce_pagination', 10 );

	/* Remove pagination on the bottom of shop page */
	remove_action( 'woocommerce_after_shop_loop', 'woocommerce_pagination', 10 );
