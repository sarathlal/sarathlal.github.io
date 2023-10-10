---
title: Get values of product custom attribute - WooCommerce
layout: post
tags:
  - WordPress
  - WooCommerce
---

When we make custom product attribute in WooCommerce, they are registered as a custom taxonomy. So we can use WordPress function `get_the_terms()` to retrieve them.

When register these custom taxonomy, WooCommerce adds a prefix of `pa_` to our custom product attribute.

So if we create an attribute called `Fabrics`, who’s slug is `fabrics`, then the custom taxonomy would be ‘pa_fabrics’. Now we are going to retrieve all terms in this attribute (`fabrics`) of a product.

	$fabric_values = get_the_terms( $product->id, 'pa_fabrics');
	 
	foreach ( $fabric_values as $fabric_value ) {
		  echo $fabric_value->name;
	}
