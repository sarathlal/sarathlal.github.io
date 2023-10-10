---
title: Make a tag based related posts list for WordPress
author: sarathlal
layout: post
tags:
  - WordPress
---
We know that the related posts & recent posts are essential for blogs. The WordPress offer a default recent post widget for us.

From WordPress plugin directory, we can download some good related posts plugins. But I like to use code snippets instead of plugins for such matters.

Today we are going to create a simple related post list for our posts. It utilize `tags` to find the related posts.

First it retrieve the post&rsquo;s tags. If a post has tags, the first one is extracted and used in a query that retrieves posts with the same tag.

By default, this code displays up to five related posts. To change this number, we want to edit line 9 of this code.

*   Open the `single.php` file in our theme.
*   Paste the following code in side the loop:
</ul>

		<h2>Related posts</h2>
		<?php
		//for use in the loop, list 5 post titles related to first tag on current post
		$tags = wp_get_post_tags($post->ID);
		if ($tags) {
		  echo 'Related Posts';
		  $first_tag = $tags[0]->term_id;
		  $args=array(
			'tag__in' => array($first_tag),
			'post__not_in' => array($post->ID),
			'showposts'=>5,
			'caller_get_posts'=>1
		   );
		  $my_query = new WP_Query($args);
		  if( $my_query->have_posts() ) {
			while ($my_query->have_posts()) : $my_query->the_post(); ?>
			  <p><a href="<?php the_permalink() ?>" rel="bookmark" title="Permanent Link to <?php the_title_attribute(); ?>"><?php the_title(); ?></a></p>
			  <?php
			endwhile;
		  }
		}
		?>

Save the file, and then reload our blog. If we have tags for our posts, we can find a list of related posts in our single posts.
