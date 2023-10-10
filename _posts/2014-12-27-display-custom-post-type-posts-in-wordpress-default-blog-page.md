---
title: Display Custom Post type posts in WordPress default blog pages
author: sarathlal
layout: post
tags:
  - WordPress
---

In default, WordPress display `post` post type in blog page. Consider that we have few custom post type like album, movie, quote etc and we want to display them in our blog page!

To get so, we want to add a small code snippet in our theme’s / child theme’s `function.php` file.

	add_filter( 'pre_get_posts', 'custom_get_posts' );

	function custom_get_posts( $query ) {

	 if ( is_home() && $query->is_main_query() )
	 $query->set( 'post_type', array( 'post', 'album', 'movie', 'quote' ) );

	 return $query;
	}

With this code snippet, now we are modifying query for blog posts with other custom post types.

If we like to display this post types in our feed also, we want to update the if statement in the above code snippet.

	if ( ( is_home() && $query->is_main_query() ) || is_feed() )

Now we have our custom post type posts in blog index page with other blog posts. This will extreemly usefull in WordPress coustomizations for Magazine and blogs.
