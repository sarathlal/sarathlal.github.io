---
title: Change shipping and billing address title - WooCommerce
layout: post
tags:
  - WooCommerce
  - WordPress
tested: WordPress 5.2, WooCommerce 3.6.5
---

![Change shipping and billing address title - WooCommerce](/images/2019/7/change-billing-shipping-address-title-woocommerce.gif)

If you like to modify the title of the addresses on the "My Account" page for WooCommerce.

	add_filter( 'woocommerce_my_account_get_addresses', 'er45d_woo_change_title_account' );
	function er45d_woo_change_title_account( $account_title ) {
		$account_title = array(
			'billing' => __( 'New Billing Address', 'text-domain' ),
			'shipping' => __( 'New Shipping Address', 'text-domain' ),
		);
		
		return $account_title;
	}
