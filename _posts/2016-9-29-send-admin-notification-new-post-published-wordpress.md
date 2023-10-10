---
title: Send admin notification when a new post published - WordPress
layout: post
tags:
  - WordPress
---

In some WordPress sites, may there will be a chance for too many editors and authors. They can add and publish the content.

In such situation, I like to notify my admin about publishing a new post. If you like to do so, use the below code snippet.

	function mquetr_notify_admin_on_publish( $new_status, $old_status, $post ) {
		$post_type = 'your_post_type';
		if ( $new_status !== 'publish' || $old_status === 'publish' )
			return;
		if ( ! $post_type = get_post_type_object( $post->post_type ) )
			return;

		// Recipient, in this case the administrator email
		$emailto = get_option( 'admin_email' );

		// Email subject, "New {post_type_label}"
		$subject = 'New ' . $post_type->labels->singular_name;

		// Email body
		$message = 'View it: ' . get_permalink( $post->ID ) . "\nEdit it: " . get_edit_post_link( $post->ID );

		wp_mail( $emailto, $subject, $message );
	}

	add_action( 'transition_post_status', 'mquetr_notify_admin_on_publish', 10, 3 );
