---
title: Get WordPress page content from Post ID using get_post()
author: 
layout: post
tags:
  - WordPress
---

We can simply extract single Page, Post or any custom post type content from its ID using get_post() function.

	<?php
	$post = get_post($id); //assuming that you already have Post ID ($id)
	setup_postdata($post);

	// display the post here
	the_title();
	the_excerpt();
	the_post_thumbnail();

	wp_reset_postdata();
	?>
