---
title: Initiate action when post was updated - WordPress
layout: post
tags:
  - WordPress
---

In one of my recent project, I have to create and update few files during post update.

The WordPress have a fantastic action hook called `save_post` for such tasks.

The `save_post` action triggered whenever a post or page is created or updated, which could be from an import, post/page edit form, xmlrpc, or post by email.

The data for the post is stored in `$_POST`, `$_GET` or the global `$post_data`, depending on the edit mode. Also this action is triggered right after the post has been saved, so we can easily access this post object by using `get_post($post_id)`.

	function my_custom_function_update( $post_id ) {

		// If this is just a revision, reject it.
		if ( wp_is_post_revision( $post_id ) )
			return;
		
		//Do your task
	}
	add_action( 'save_post', 'my_custom_function_update' );


### Example

	function my_project_updated_send_email( $post_id ) {

		if ( wp_is_post_revision( $post_id ) )
			return;

		$post_title = get_the_title( $post_id );
		$post_url = get_permalink( $post_id );
		$subject = 'A post has been updated';

		$message = "A post has been updated on your website:\n\n";
		$message .= $post_title . ": " . $post_url;

		wp_mail( 'admin@example.com', $subject, $message );
	}
	add_action( 'save_post', 'my_project_updated_send_email' );
