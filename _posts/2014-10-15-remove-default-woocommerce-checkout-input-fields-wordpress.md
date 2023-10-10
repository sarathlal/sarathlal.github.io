---
title: 'Remove default WooCommerce checkout input fields &#8211; WordPress'
author: sarathlal
layout: post
tags:
  - WooCommerce
  - WordPress
---
In default, WooCoomerce checkout page show different input fields for shipping and billing. Some of them have no roles in some online stores because they sell entirely different products & services.

If we have such a scene, hiding these unnecessary fields is always good for our store. But WooCommerce don&#8217;t have any option to disable / hide them from back end.

So now we are going to add few code lines in our theme&#8217;s / child theme&#8217;s `functions.php` file to remove these fields.

    
    add_filter( 'woocommerce_checkout_fields' , 'custom_override_checkout_fields' );
    
    function custom_override_checkout_fields( $fields ) {
        unset($fields['billing']['billing_first_name']);
        unset($fields['billing']['billing_last_name']);
        unset($fields['billing']['billing_company']);
        unset($fields['billing']['billing_address_1']);
        unset($fields['billing']['billing_address_2']);
        unset($fields['billing']['billing_city']);
        unset($fields['billing']['billing_postcode']);
        unset($fields['billing']['billing_country']);
        unset($fields['billing']['billing_state']);
        unset($fields['billing']['billing_phone']);
        unset($fields['order']['order_comments']);
        unset($fields['billing']['billing_address_2']);
        unset($fields['billing']['billing_postcode']);
        unset($fields['billing']['billing_company']);
        unset($fields['billing']['billing_last_name']);
        unset($fields['billing']['billing_email']);
        unset($fields['billing']['billing_city']);
        return $fields;
    }
    

The above code will remove all billing input fields. So only unset the items not required.

If you like to remove fields from shipping section, we can use the same filter with few changes on parameters.

    
    add_filter( 'woocommerce_checkout_fields' , 'custom_override_checkout_fields' );
    
    function custom_override_checkout_fields( $fields ) {
        unset($fields['shipping']['shipping_first_name']);
        unset($fields['shipping']['shipping_last_name']);
        unset($fields['shipping']['shipping_company']);
        return $fields;
    }
