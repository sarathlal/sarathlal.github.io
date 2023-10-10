---
title:  Change WooCommerce default product sorting labels
layout: post
tags:
  - WordPress
  - WooCommerce
---

The WooCommerce have 6 default product sorting option in archives and shop pages. They have default labels and in some WooCommerce customization, I want to change these labels.

To Quickly change translatable strings in theme or plugins, we can use WordPress `gettext` filter. So now we are going to use this filter to change product sorting labels in WooCommerce by adding a little code snippet in our theme's `functions.php` file.

	add_filter( 'gettext', 'theme_sort_change', 20, 3 );
	
	function theme_sort_change( $translated_text, $text, $domain ) {
		if ( is_woocommerce() ) {
			switch ( $translated_text ) {
			case 'Sort by price: low to high' :
			$translated_text = __( 'Sort by Price: Lowest to Highest', 'theme_text_domain' );
			break;
			case 'Sort by price: high to low' :
			$translated_text = __( 'Sort by Price: Highest to Lowest', 'theme_text_domain' );
			break;
			case 'Sort by newness' :
			$translated_text = __( 'Sort by Newness', 'theme_text_domain' );
			break;
			case 'Sort by title: Alphabetically' :
			$translated_text = __( 'Sort by Title: Alphabetically', 'theme_text_domain' );
			break;
			case 'Sort by title: Reverse-Alphabetically' :
			$translated_text = __( 'Sort by Title: Reverse-Alphabetically', 'theme_text_domain' );
			break;
			case 'Default sorting' :
			$translated_text = __( 'Default Sorting', 'theme_text_domain' );
			break;
			}
		}
	return $translated_text;
	}
