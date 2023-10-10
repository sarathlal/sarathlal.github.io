---
title:  Change Proceed to Checkout text in WooCommerce Cart page
layout: post
tags:
  - WordPress
  - WooCommerce
---

To change Proceed To Checkout text in Cart page, use one of the below code snippet ( as per the WooCommerce version ) in our theme's `functions.php` file.

### The Old Version (Up to WooCommerce 2.3.7)

	remove_action( 'woocommerce_proceed_to_checkout', 'woocommerce_button_proceed_to_checkout', 10 ); 
	add_action('woocommerce_proceed_to_checkout', 'ld_woo_custom_checkout_button_text');

	function ld_woo_custom_checkout_button_text() {
		$checkout_url = WC()->cart->get_checkout_url();
		?> 
		<a href="<?php echo $checkout_url; ?>" class="checkout-button button alt wc-forward"><?php  _e( 'Check On Out', 'woocommerce' ); ?></a> 
	<?php }

### From WooCommerce 2.3.8

	function woocommerce_button_proceed_to_checkout() {
       $checkout_url = WC()->cart->get_checkout_url();
       ?>
       <a href="<?php echo $checkout_url; ?>" class="checkout-button button alt wc-forward"><?php _e( 'Check On Out', 'woocommerce' ); ?></a>
       <?php
    }
