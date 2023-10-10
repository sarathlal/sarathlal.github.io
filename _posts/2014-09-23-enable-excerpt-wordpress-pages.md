---
title: Enable Excerpt in WordPress pages
author: sarathlal
layout: post
tags:
  - WordPress
---
In default, the excerpts are only available for WordPress posts.

But we can easily enable this excerpt functionality to our WordPress pages with few lines of codes.

Just add below code snippet in to WordPress theme&#8217;s / child theme&#8217;s `functions.php` file.

	add_action( 'init', 'add_excerpt_to_pages' );
	function add_excerpt_to_pages() {
	 add_post_type_support( 'page', 'excerpt' );
	}
