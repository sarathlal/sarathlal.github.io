---
title: Add actions based on WooCoomerce order status
layout: post
tags:
  - WordPress
  - WooCommerce
---

Have you ever tried to do some actions based on WooCommerce order status? Here is the examples for whole hooks that is available during WooCommerce order status changes.
	
	// Order status - `pending`
	add_action( ‘woocommerce_order_status_pending', ‘order_pending');
    function order_pending($order_id) {
		
		// Do your logic here
		
    }
    
    
    // Order status - `failed`
    add_action( ‘woocommerce_order_status_failed', ‘order_failed');
    function order_failed($order_id) {
		
		// Do your logic here
		
    }
    
    // Order status - `on-hold`
    add_action( 'woocommerce_order_status_on-hold', ‘order_hold');
    function order_hold($order_id) {
		
		// Do your logic here
		
    }
    
    // Order status - `processing`
    add_action( ‘woocommerce_order_status_processing', ‘order_processing');
    function order_processing($order_id) {
		
		// Do your logic here
		
    }
    
    // Order status - `completed`
    add_action( ‘woocommerce_order_status_completed', ‘order_completed');
    function order_completed($order_id) {
		
		// Do your logic here
		
    }
    
    // Order status - `refunded`
    add_action( ‘woocommerce_order_status_refunded', ‘order_refunded');
    function order_refunded($order_id) {
		
		// Do your logic here
		
    }
    
    // Order status - `cancelled`
    add_action( ‘woocommerce_order_status_cancelled', ‘order_cancelled');
    function order_cancelled($order_id) {
		
		// Do your logic here
		
    }
