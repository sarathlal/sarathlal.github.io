---
title: Redirect single pages of post type in to post type archive page - WordPress
layout: post
tags:
  - WordPress
tested: WordPress 5.2
---

In WordPress, if our post type is public, in default, a single page view will be available for all posts in that post type.

If we don't need a single view of post type, it is better to make post type, not as public. In `register_post_type` hook, there is an argument called `public` & we have to set that value as false.

But now I need to make one of my custom post types as public & the same time, I need to remove the single page view of that custom post type. Below you can find the code snippet that I have used for that purpose.

	add_action( 'template_redirect', function() {
		$post_type = 'board_member';
		if ( is_singular($post_type) ) {
			global $post;
			$redirectLink = get_post_type_archive_link( $post_type );
			wp_redirect( $redirectLink, 302 );
			exit;
		}
	});
