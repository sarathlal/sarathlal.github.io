---
title: Customize / Modify WooCommerce REST API response using filter
layout: post
tags:
  - WooCommerce
  - WordPress
---

In some WooCommerce customization projects, I need to modify the REST API response for order, product & customer request. The filter functions for these 3 requests are given below.

### Modify response on get customer request

	curl https://example.com/wp-json/wc/v3/customers/<user_id> \
		-u consumer_key:consumer_secret

#### Filter function

	add_filter('woocommerce_rest_prepare_customer', 'filter_response', 10, 3);
	function filter_response($response, $user_data, $request){
		// Customize response data here
		$user_id = $user_data->ID;
		
		$response->data["custom"] = 3;
		return $response;
	}

### Modify response on get product request

	curl https://example.com/wp-json/wc/v3/products/<product_id> \
		-u consumer_key:consumer_secret

#### Filter function

	add_filter('woocommerce_rest_prepare_product_object', 'filter_product_response', 10, 3);
	function filter_product_response($response, $post, $request){
		// Customize response data here
		$product_id = $post->get_id();
		
		$response->data["custom"] = 12;
		return $response;
	}

### Modify response on get order request

	curl https://example.com/wp-json/wc/v3/orders/<order_id> \
		-u consumer_key:consumer_secret

#### Filter function

	add_filter('woocommerce_rest_prepare_shop_order_object', 'filter_order_response', 10, 3);
	function filter_($response, $post, $request){
	    // Customize response data here
	    $order_id = $post->get_id();

	    $response->data["custom"] = 12;
	    return $response;
	}
