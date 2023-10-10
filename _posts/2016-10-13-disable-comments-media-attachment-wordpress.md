---
title: Disable Comments on Media Attachment Page - WordPress
layout: post
tags:
  - WordPress
---

When we upload an image in to WordPress media, the WordPress save it as a post with the post type as `attachment`. So we can access each image in separate single pages same like single post or single page.

In default, WordPress allow users to add comments on each of this attachment posts.

But I like to disable this commenting options on attachment post type because it is unnecessary for a normal CMS sites.

We can use an action hook to done this job.

	function disable_media_comments( $post_id ) {
		if( get_post_type( $post_id ) == 'attachment' ) {
			wp_die("Comment not allowed.");
		}
		return $open;
	}
	add_action( 'pre_comment_on_post', 'disable_media_comments' );
	
If you already added images on WordPress media, you have to close the comment system for these uploaded images. We have to apply a simple SQL query in our database to do so.

	UPDATE `wp_posts` SET `comment_status` = 'closed' WHERE `post_type` = 'attachment' AND `comment_status` = 'open';
