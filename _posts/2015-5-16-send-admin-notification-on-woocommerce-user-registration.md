---
title:  Send notification to administrator on WooCommerce user registration
layout: post
tags:
  - WordPress
  - WooCommerce
---

In WordPress sites, if a new user was registered, the WordPress will send a notification to administrator. But if we are using WooCommerce, user registration will done through `process_registration` action in WooCommerce. At that time, WordPress never send email notification to admin about new user.

So now we are going to override this functionality by adding a little code snippet to our theme's / child theme's `functions.php` file.

	add_action('woocommerce_created_customer', 'admin_email_on_registration', 10 , 1);
	function admin_email_on_registration( $customer_id) {
		wp_new_user_notification( $customer_id );
	}

The `woocommerce_created_customer` is a hook which is called during new user registration by WooCommerce. In default, it only sends notification to customers. So we just call the WordPress default new user notification function - `wp_new_user_notification()` on WooCommerce user registration process to send notification to administrator.
