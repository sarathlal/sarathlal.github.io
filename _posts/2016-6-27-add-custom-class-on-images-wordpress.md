---
title: Add custom class on images - WordPress
layout: post
tags:
  - WordPress
---

When we attach & insert an image in to WordPress post / page, the WordPress will add some default classes to that image.

In some situations, I want to add custom class to all images on WordPress site. To do so, we can use a filter function.

	function add_custom_image_class($class) {
		$class .= ' my-custom-class';
		return $class;
	}
	add_filter('get_image_tag_class', 'add_custom_image_class' );
	
If we want to add custom class on specific images like thumbnails only, there is option to pass class name as parameter in such function call.

	the_post_thumbnail('full', array( 'class'	=> "my-custom-class my-custom-class-2"));


