---
title: How to change Add to cart button text in WooCommerce
author: sarathlal
layout: post
tags:
  - WooCommerce
  - WordPress
---
Recently, I want to customize a home stay online store that sell rooms. They want to change there add to cart button text &#8211; &#8220;Add to Cart&#8221; in to &#8220;Book Now&#8221;.

To change this text, we can use a WordPress filter hook in our child theme&#8217;s functions.php file. Just copy paste below code snippets in to that file.

    add_filter( 'woocommerce_product_single_add_to_cart_text', 'woo_custom_single_cart_button_text' ); // For single product
    function woo_custom_single_cart_button_text() {
    return __( 'Book Now', 'woocommerce' );
    }
    
    add_filter( 'woocommerce_product_add_to_cart_text', 'woo_custom_cart_button_text' ); // For Catalog and index pages
    function woo_custom_cart_button_text() {
    return __( 'Book Now', 'woocommerce' );
    }
