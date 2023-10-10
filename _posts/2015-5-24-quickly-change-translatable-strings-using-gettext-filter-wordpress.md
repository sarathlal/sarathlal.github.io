---
title:  Quickly change translatable strings using gettext filter -  WordPress
layout: post
tags:
  - WordPress
---

To translate or change text within a WordPress theme / plugin, we want to edit the theme / plugin PO file ( if the theme has been localized ).

Consider that we have to quickly change a few words on our site though without editing the PO file. We can easily do this by using a WordPress function and `gettext` filter that will translate / replace any text that has been localized.

### Example:

In WooCommerce single product template files, we have a statement like below on `related.php` file. 

	<?php _e( 'Related Products', 'woocommerce' ); ?>

We can easily translate these strings by adding a filter to our theme's `functions.php` file.


	/*
	 * Change text strings
	 */
	function my_text_strings( $translated_text, $text, $domain ) {
		switch ( $translated_text ) {
			case 'Related Products' :
				$translated_text = __( 'Check out these related products', 'woocommerce' );
				break;
		}
		return $translated_text;
	}
	add_filter( 'gettext', 'my_text_strings', 20, 3 );
	
Too simple! We can add as many translations to that filter by adding new case statements.
