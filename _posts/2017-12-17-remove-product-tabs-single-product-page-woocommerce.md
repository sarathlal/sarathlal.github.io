---
title: Remove product tabs in single product page - WooCommerce
layout: post
tags:
  - WordPress
  - WooCommerce
---

If we added proper content, there will be 3 tabs in WooCommerce single product page.

1. Product Description - Post content
2. Additional Information -  Attributes & Values
3. Reviews

![WooCommerce Product Tabs](/images/2017/product-tabs-woocommerce.png)

If you like to remove any of the one or whole, you can use below code in your theme's `functions.php` or in your custom module file.


	add_filter( 'woocommerce_product_tabs', 'd3b56mn_remove_product_tabs', 98 );

	function d3b56mn_remove_product_tabs( $tabs ) {
		unset( $tabs['description'] );      	// Remove the description tab
		unset( $tabs['reviews'] ); 			// Remove the reviews tab
		unset( $tabs['additional_information'] );  	// Remove the additional information tab
		return $tabs;
	}
