---
title: 'Display posts published one year ago - WordPress'
author: sarathlal
layout: post
tags:
  - WordPress
---
If we have a large collection of posts, often there is a chance to ignored them by visitors because most of them only visits the freshest content.

In such situations, if we can creatively present our old posts, they help to keep our visitors to read few more posts from our blog.

The related posts, recent posts & random posts lists are consider as a effective methods in such situations.

Additional to these list, today we are going to display posts that were published over a year ago. This is a simple code snippet & we can insert it on our sidebar or `single.php` file.

	<?php
	$current_day = date('j');
	$last_year = date('Y')-1;
	query_posts('day='.$current_day.'&year='.$last_year);
	if (have_posts()):
		while (have_posts()) : the_post();
		   the_title();
		   the_excerpt();
		endwhile;
	endif;
	?>

This code snippet is simple to understand the logic. First it store current day in `$current_day` variable, then calculate the previous year by decrementing 1 from current year & store it in `$last_year` variable.

At last it do a query to retrieve posts with day & year parameter with these variable. Then list post title & excerpt on pages.
