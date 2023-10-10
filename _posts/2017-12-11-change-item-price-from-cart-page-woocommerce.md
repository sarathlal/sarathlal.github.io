---
title: Change item price from cart page - WooCommerce
layout: post
tags:
  - WordPress
  - WooCommerce
---

Have you ever faced a situation to change item price in WooCommerce cart page.

Recently, one of my client requested to do this tweak in his store. Update the code with your conditions & put it in your theme's `functions.php` file or your custom module file.

	add_action( 'woocommerce_before_calculate_totals', 'bthu9v_recalc_price' );

	function bthu9v_recalc_price( $cart_object ) {
		foreach ( $cart_object->get_cart() as $hash => $value ) {
			$value['data']->set_price( 10 );
		}
	}
