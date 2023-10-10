---
title: Add phone number to the output of the addresses on the "My Account" page - WooCommerce
layout: post
tags:
  - WooCommerce
  - WordPress
tested: WordPress 5.2, WooCommerce 3.6.5
---

![Add phone number to the output of the addresses on the "My Account" page - WooCommerce](/images/2019/7/add-phone-number-output-addresses-my-account-page-woocommerce.gif)

We need to add 3 filters to modify the output of the addresses on the "My Account" page/shortcode for WooCommerce.

First, we will need to use `woocommerce_my_account_my_address_formatted_address` to populate any new values we want to add.

	add_filter( 'woocommerce_my_account_my_address_formatted_address', 'er34d_formatted_address',10, 3 );
	
	function er34d_formatted_address( $args, $customer_id, $name ){
		// the phone is saved as billing_phone and shipping_phone
		$args['phone'] = get_user_meta( $customer_id, $name . '_phone', true );
		return $args;
	} 

Next use `woocommerce_localisation_address_formats` to modify the formatting of the address. We have do this as per country locale. But now I ignore that condition.


	// modify the address formats
	add_filter( 'woocommerce_localisation_address_formats', '3e45_localisation_address_formats');

	function 3e45_localisation_address_formats( $formats ){
		foreach ( $formats as $key => &$format ) {
			// put a break and then the phone after each format.
			$format .= "\n{phone}";
		}
		return $formats;
	}


Last, we need to update `woocommerce_formatted_address_replacements` to have WooCommerce replace your replacement string with the actual data.


	// add the replacement value
	add_filter( 'woocommerce_formatted_address_replacements', '3er45_formatted_address_replacements', 10, 2 );

	function 3er45_formatted_address_replacements( $replacements, $args ){
		// we want to replace {phone} in the format with the data we populated
		$replacements['{phone}'] = $args['phone'];
		return $replacements;
	}
