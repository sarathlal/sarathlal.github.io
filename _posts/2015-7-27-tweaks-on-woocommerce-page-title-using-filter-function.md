---
title:  Tweaks on WooCommerce page title using woocommerce_page_title filter
layout: post
tags:
  - WordPress
  - WooCommerce
---

In one of my recent WooCommerce project, I want to add a text string with all category archive page's title. On the same project, also I want to improve the title for product search result pages.

In WooCommerce, we have a function called `woocommerce_page_title` and we can use this one to apply changes on WooCommerce page titles.

### examples

#### Add a string with category archive page titles.

	function change_woocommerce_category_page_title( $page_title )
	{
		if ( is_product_category() ) {
			
			$page_title = "My String " . $page_title;
			
		}
		return $page_title;
	}

	// add the filter
	add_filter( 'woocommerce_page_title', 'change_woocommerce_category_page_title', 10, 1 );


####  Better title for search result page

	function better_woocommerce_search_result_title( $page_title )
	{
		if ( is_search() ) {
			if (! get_search_query()) {
				$page_title = sprintf( __( 'Search Results: “All Products”', 'woocommerce' ), get_search_query() );
			} else {
				$page_title = sprintf( __( 'Search Results: “%s”', 'woocommerce' ), get_search_query() );
			}
		}
		return $page_title;
	}

	// add the filter
	add_filter( 'woocommerce_page_title', 'better_woocommerce_search_result_title', 10, 1 );

There is too many creative ways to use this filter on our WooCommerce page title. Just try to tweak the code and it will give out standing page title for our stores.
