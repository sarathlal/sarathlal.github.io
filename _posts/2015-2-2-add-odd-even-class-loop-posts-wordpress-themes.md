---
title: Add Odd or Even class to posts in loop - WordPress Themes
author: sarathlal
layout: post
tags:
  - WordPress
---

In Some WordPress theme customizations, I want to give different styles for odd/even post. So adding a class (odd or even) to my repeating element inside the loop is always a handy function.

In such cases, we can use one of the `WP Query` class property - `$current_post`. This can provide the current post index number & we can use that one to check whether the post is odd or even.

	<?php echo ($loop->current_post%2 == 0?'odd':'even'); ?>

#### example

	<?php
	// The Query
	$the_query = new WP_Query( $args );

	// The Loop
	if ( $the_query->have_posts() ) {
		echo '<ul>';
		while ( $the_query->have_posts() ) {
			$the_query->the_post();
			
			?>
			<li class="<?php echo ($loop->current_post%2 == 0?'odd':'even'); ?>">
				<?php
					echo get_the_title();
				?>
			</li>
			<?php
		}
		echo '</ul>';
	} else {
		// no posts found
	}
	/* Restore original Post Data */
	wp_reset_postdata();

In the above example. I added odd or even class to repeating list item - `<li>` element according to post index.
