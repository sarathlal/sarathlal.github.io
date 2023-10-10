---
title: Show SKU with product names in cart & checkout - WooCommerce
layout: post
tags:
  - WooCommerce
  - WordPress
tested: WordPress 5.8, WooCommerce 5.9
---

Recently, one of my clients requested to display product SKU with product names in cart & checkout pages.

Here is the solution to achieve the requirement. You have to use the code snippet in your child theme's functions.php file.

    add_filter( 'woocommerce_cart_item_name', 'tl3er4_cart_item_name', 10, 3 );
    function tl3er4_cart_item_name( $item_name,  $cart_item,  $cart_item_key ) {
	    // Modify page slug
	    if ( is_page( array( 'cart', 'quick-order' ) ) ) {
		    $product = $cart_item['data'];
		    if($product->get_sku()){
			    echo $item_name.' ('.$product->get_sku().')';
		    }else{
			    echo $item_name;	
		    }
	    }else{
		    echo $item_name;
	    }
    }
