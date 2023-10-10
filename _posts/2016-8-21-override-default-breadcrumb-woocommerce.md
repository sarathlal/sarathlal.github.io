---
title: Override default breadcrumb - WooCommerce
layout: post
tags:
  - WordPress
  - WooCommerce
---

In default, WooCommerce display a breadcrumb on its pages. It help user to realize the current location & navigate to parent pages.

In some projects, clients request few modifications on default breadcrumb like a separate delimiter, adding a separate class etc.

Below, there is a small code snippet that will useful in such situations.

	add_filter( 'woocommerce_breadcrumb_defaults', 't9fe9_woocommerce_breadcrumbs' );
	function t9fe9_woocommerce_breadcrumbs() {
		return array(
				'delimiter'   => ' > ',
				'wrap_before' => '<div class="custom-wrap"><nav class="woocommerce-breadcrumb" itemprop="breadcrumb">',
				'wrap_after'  => '</nav></div>',
				'before'      => '',
				'after'       => '',
				'home'        => _x( 'Home', 'breadcrumb', 'woocommerce' ),
			);
	}
