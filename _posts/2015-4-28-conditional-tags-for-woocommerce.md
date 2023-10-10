---
title: Conditional Tags for WooCommerce
layout: post
tags:
  - WordPress
  - WooCommerce
---

The conditional tags help us to change what content is displayed and how that content is displayed on a particular page depending on what conditions that page matches.

### A WooCommerce page

    is_woocommerce()

Returns true if on a page which uses WooCommerce templates (cart and checkout are standard pages with shortcodes and thus are not included).

### The main shop page

    is_shop()

Returns true when on the product archive page (shop).

### A product category page

    is_product_category()

Returns true when viewing a product category archive.

    is_product_category( 'shirts' )

When the product category page for the ‘shirts’ category is being displayed.

    is_product_category( array( 'shirts', 'games' ) )

When the product category page for the ‘shirts’ or ‘games’ category is being displayed.

### A product tag page

    is_product_tag()

Returns true when viewing a product tag archive

    is_product_tag( 'shirts' )

When the product tag page for the ‘shirts’ tag is being displayed.

    is_product_tag( array( 'shirts', 'games' ) )

When the product tag page for the ‘shirts’ or ‘games’ tags is being displayed.

### A single product page

    is_product()

Returns true on a single product page. Wrapper for is_singular.

### The cart page

    is_cart()

Returns true on the cart page.

### The checkout page

    is_checkout()

Returns true on the checkout page.

### Customer account pages

    is_account_page()

Returns true on the customer’s account pages.

### An endpoint

    is_wc_endpoint_url()

Returns true when viewing a WooCommerce endpoint

    is_wc_endpoint_url( 'order-pay' )

When the endpoint page for order pay is being displayed.

    is_wc_endpoint_url( 'order-received' )

When the endpoint page for order received is being displayed.

    is_wc_endpoint_url( 'view-order' )

When the endpoint page for view order is being displayed.

    is_wc_endpoint_url( 'edit-account' )

When the endpoint page for edit account is being displayed.

    is_wc_endpoint_url( 'edit-address' )

When the endpoint page for edit address is being displayed.

    is_wc_endpoint_url( 'lost-password' )

When the endpoint page for lost password is being displayed.

    is_wc_endpoint_url( 'customer-logout' )

When the endpoint page for customer logout  is being displayed.

    is_wc_endpoint_url( 'add-payment-method' )

When the endpoint page for add payment method is being displayed.

### An ajax request

    is_ajax()

Returns true when the page is loaded via ajax.

### Example

	if ( is_product_category() ) {
	  
	  if ( is_product_category( 'shirts' ) ) {
		echo 'Hi! Take a look at our sweet tshirts below.';
	  } elseif ( is_product_category( 'games' ) ) {
		echo 'Hi! Hungry for some gaming?';
	  } else {
		echo 'Hi! Check our our products below.';
	  }

	}
