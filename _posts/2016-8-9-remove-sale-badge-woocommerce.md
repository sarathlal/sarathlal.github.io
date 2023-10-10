---
title: Remove Sale badge - WooCommerce
layout: post
tags:
  - WordPress
  - WooCommerce
---

In WooCommerce, if an item have a sale price (special price), a sale badge will be visible on archive pages and single product view page.

We can easily remove this sale badge.

	// Remove "Sale" badge from product archive page
	remove_action( 'woocommerce_before_shop_loop_item_title', 'woocommerce_show_product_loop_sale_flash', 10 );

	// Remove "Sale" badge from product single page
	remove_action( 'woocommerce_before_single_product_summary', 'woocommerce_show_product_sale_flash', 10 );
