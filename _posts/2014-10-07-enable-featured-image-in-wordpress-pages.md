---
title: Enable featured image in WordPress pages
author: sarathlal
layout: post
tags:
  - WordPress
---
In default, the featured image is only available for WordPress post.

But we can easily enable featured image for WordPress pages also. Just add below code snippet in to our theme&#8217;s / child theme&#8217;s `functions.php` file.

	add_action( 'init', 'add_featured_image_to_pages' );
	function add_featured_image_to_pages() {
	 add_theme_support( 'post-thumbnails', array( 'post', 'page' ) );
	}

&nbsp;
