---
title: Display total items and total price in cart - WooCommerce
layout: post
tags:
  - WooCommerce
  - WordPress
---

In some WooCommerce theme customizations, I want to display total items and total price in cart on some location like page header etc. So just use below code snippet in our template files.

	<a class="cart-contents" href="<?php echo WC()->cart->get_cart_url(); ?>" title="<?php _e( 'View your shopping cart' ); ?>"><?php echo sprintf (_n( '%d item', '%d items', WC()->cart->cart_contents_count ), WC()->cart->cart_contents_count ); ?> - <?php echo WC()->cart->get_cart_total(); ?></a>
