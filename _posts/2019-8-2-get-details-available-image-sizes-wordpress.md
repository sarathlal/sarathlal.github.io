---
title: Get details about available image sizes - WordPress
layout: post
tags:
  - WordPress
tested: WordPress 5.2
---

Recently, when I develop a WordPress theme, I need details about all available image sizes for the theme customizer module. I need details about custom image sizes added by other plugins (Eg. WooCommerce etc) & default WordPress image sizes.

The WordPress core doesn't have a native method for getting all the details. So I used the below function.


	/**
	 * Get all the registered image sizes along with their dimensions
	 *
	 * @global array $_wp_additional_image_sizes
	 *
	 * @link http://core.trac.wordpress.org/ticket/18947 Reference ticket
	 *
	 * @return array $image_sizes The image sizes
	 */
	function _get_all_image_sizes() {
		global $_wp_additional_image_sizes;

		$default_image_sizes = get_intermediate_image_sizes();

		foreach ( $default_image_sizes as $size ) {
			$image_sizes[ $size ][ 'width' ] = intval( get_option( "{$size}_size_w" ) );
			$image_sizes[ $size ][ 'height' ] = intval( get_option( "{$size}_size_h" ) );
			$image_sizes[ $size ][ 'crop' ] = get_option( "{$size}_crop" ) ? get_option( "{$size}_crop" ) : false;
		}

		if ( isset( $_wp_additional_image_sizes ) && count( $_wp_additional_image_sizes ) ) {
			$image_sizes = array_merge( $image_sizes, $_wp_additional_image_sizes );
		}

		return $image_sizes;
	}


The output will be an array like below one.

	Array
	(
		[thumbnail] => Array
			(
				[width] => 150
				[height] => 150
				[crop] => 1
			)

		[medium] => Array
			(
				[width] => 300
				[height] => 300
				[crop] => 
			)

		[medium_large] => Array
			(
				[width] => 768
				[height] => 0
				[crop] => 
			)

		[large] => Array
			(
				[width] => 1024
				[height] => 1024
				[crop] => 
			)

	)
