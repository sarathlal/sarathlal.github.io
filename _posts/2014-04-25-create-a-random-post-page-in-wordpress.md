---
title: Create a random post page in WordPress
author: sarathlal
layout: post
tags:
  - WordPress
---
Getiing some things in a random order is always interesting. So today we are going to make a random post page in WordPress.

The random post page means, when a user visit that page, he can see a random post from our WordPress blog. Then if he try to refresh that page again, an another random post is delivered to him.

If we have a good collection of blog posts, this random post page can offer a good reading experience for our visitors.

Any way, now we are going to make it happen with a small code snippet.

First we want to make a custom post template for our random post page in our child theme folder. In that page, add a simple WordPress loop to get random posts from our post collection.

	<?php
	query_posts(array('orderby' => 'rand', 'showposts' => 5));
	if (have_posts()) :
		while (have_posts()) : the_post(); ?>

			<h1><a href="<?php the_permalink() ?>"><?php the_title(); ?></a></h1>

			<?php the_content(); ?>

		<?php endwhile;
	endif; ?>

This query only display the titles of 5 random post in that page. But we can change the number of posts and add post content or excerpt with these random posts according to our intension.
