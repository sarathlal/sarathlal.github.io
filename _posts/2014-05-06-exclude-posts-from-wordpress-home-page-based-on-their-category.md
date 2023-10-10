---
title: Exclude posts from WordPress home page based on their category
author: sarathlal
layout: post
tags:
  - WordPress
---
There may be situations where we want to exclude posts from the WordPress home page based on their category.

To get this done, first we want to find template file for home page. Very often, it will be `index.php` in our theme folder. Then find the below line of code on it.

	<?php if ( have_posts() ) : while ( have_posts() ) : the_post(); ?>

Just replace this line with below code.

	<?php query_posts('cat=-4'); ?>
	<?php if ( have_posts() ) : while ( have_posts() ) : the_post(); ?>

This will exclude posts in category number four from being displayed on the home page.
