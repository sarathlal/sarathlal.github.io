---
title: 'Get posts with custom field & specific value - WordPress'
author: sarathlal
layout: post
tags:
  - WordPress
---
The custom field is an amazing option in WordPress blog engine. We can make hundreds of useful applications & tricks with custom field to improve functionality of WordPress.

Today we are going to use this custom field in a creative way. We try to output a list of posts with a specific custom field and specific value through a simple hack.

I already say that this is too simple. We just want to add some new parameters with loop used to query posts.

	<?php query_posts('meta_key=review_type&meta_value=movie');  ?>
	<?php if (have_posts()) : ?>
	<?php while (have_posts()) : the_post(); ?>

To get posts with a specific custom field and specific value, we use the `query_posts()` function with the `meta_key` and `meta_value` parameters. The `meta_key` value is the name of the desired custom field, and `meta_value` is the desired value.
