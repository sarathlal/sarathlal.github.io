---
title: Change WooCommerce pagination next and previous text
layout: post
tags:
  - WordPress
  - WooCommerce
---

In the WooCommerce archive pages, there is a default pagination with page numbers. In that pagination, there is also a `Next` and `Previous` page links related with current page.

In some WooCommerce customizations, client suggest to change these texts. We can use below code snippet to change WooCommerce pagination next and previous text.

	add_filter( 'woocommerce_pagination_args' , 'tq73et_override_pagination_args' );
	function tq73et_override_pagination_args( $args ) {
		$args['prev_text'] = __( 'Your Prev' );
		$args['next_text'] = __( 'Your Next' );
		return $args;
	}
