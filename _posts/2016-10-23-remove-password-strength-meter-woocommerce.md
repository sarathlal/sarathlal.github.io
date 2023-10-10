---
title: Remove password strength meter - WooCommerce
layout: post
tags:
  - WordPress
  - WooCommerce
---

In WooCommerec 2.5, they have added a password strength meter for user accounts. Now when a user can only create an account if they have a strong password.

Some times, it is annoying & it can reduce our sales. Be aware that security is the top but user interface is also matter.

So if you like to completely remove this password strength meter, use below code snippet.

	function wc_dq25t_remove_password_strength() {
		if ( wp_script_is( 'wc-password-strength-meter', 'enqueued' ) ) {
			wp_dequeue_script( 'wc-password-strength-meter' );
		}
	}
	add_action( 'wp_print_scripts', 'wc_dq25t_remove_password_strength', 100 );
