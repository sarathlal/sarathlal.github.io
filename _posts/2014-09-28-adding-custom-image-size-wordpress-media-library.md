---
title: Adding custom image size for WordPress media Library
author: sarathlal
layout: post
tags:
  - WordPress
---
To add new custom image size for WordPress media gallery, we can use add\_image\_size() function.

	<?php add_image_size( $name, $width, $height, $crop ); ?>

####  Example code in theme&#8217;s functions.php file

    add_image_size( 'category-thumb', 300,160 ); // 300 pixels wide and 160 pixels height - resized
    add_image_size( 'homepage-thumb', 220, 180, true ); // 220 pixels wide and 180 pixels height - cropped
    

####  Different crop modes

1. Set the image size by resizing the image proportionally (without distorting it):

		add_image_size( 'custom-size', 220, 180 ); // 220 pixels wide by 180 pixels tall, soft proportional crop mode

2. Set the image size by cropping the image (not showing part of it):

		add_image_size( 'custom-size', 220, 180, true ); // 220 pixels wide by 180 pixels tall, hard crop mode

3. Set the image size by cropping the image and defining a crop position:

		add_image_size( 'custom-size', 220, 220, array( 'left', 'top' ) ); // Hard crop left top
    

####  Using the New Image Sizes in WordPress

1. For Featured Images

		<?php 
		if ( has_post_thumbnail() ) { 
		 the_post_thumbnail( 'your-custom-size-name' ); 
		}
		?>

2. For General Media (PHP/Templates)

		<?php echo wp_get_attachment_image( $post-id, 'your-custom-size-name' ); ?>
