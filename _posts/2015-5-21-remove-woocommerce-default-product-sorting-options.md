---
title:  Remove WooCommerce default product sorting options
layout: post
tags:
  - WordPress
  - WooCommerce
---

The default WooCommerce product sorting drop down list has 6 sorting options,

1. Default Sorting.
2. Sort by popularity.
3. Sort by average rating.
4. Sort by newness.
5. Sort by price: low to high.
6. Sort by price: high to low.


Now we are going to remove some of them in our shop by using WooCommerce filter hook, `woocommerce_catalog_orderby`. Add below code snippet to your theme's `functions.php` file.


	// Modify the default WooCommerce orderby dropdown

	function my_woocommerce_catalog_orderby( $orderby ) {
		unset($orderby["menu_order"]);	// Remove "Default sorting"
		unset($orderby["popularity"]);	// Remove "Sort by popularity"
		unset($orderby["rating"]);		// Remove "Sort by average rating"
		unset($orderby["date"]);		// Remove "Sort by newness"
		unset($orderby["price"]);		// Remove "Sort by price: low to high"
		unset($orderby["price-desc"]);	// Remove "Sort by price: high to low"
		return $orderby;
	}
	add_filter( "woocommerce_catalog_orderby", "my_woocommerce_catalog_orderby", 20 );

The above code will unset all options in dropdown list. So only unset the items you don't need.
