---
title: Add TinyMCE WYSIWYG (Rich text area) meta box - WordPress
layout: post
tags:
  - WordPress
---

Have you ever tried to add rich text area meta box in your post editing screen? Now the WordPress improved its `wp_editor` function & it is very easy to create new WYSIWYG meta box in WordPress admin screen.

	wp_editor( $content, $editor_id, $settings = array() );

The parameter, `$settings` is an array of arguments. More details are available in [WordPress Codex page](https://codex.wordpress.org/Function_Reference/wp_editor#Parameters){:target="_blank"}.

Below you can find an example code snippet that add a new WYSIWYG meta box - `Notes`, in the `post` post type.

	add_action( 'add_meta_boxes', 'post_note_meta_box_add' );
	function post_note_meta_box_add()
	{	
		// Add new meta box
		add_meta_box( '_post_note', 'Notes', 'render_post_note_meta_box', 'post', 'normal', 'default' );
	}

	function render_post_note_meta_box()
	{
		global $post;
		// Get saved meta data
		$post_note_meta_content = get_post_meta($post->ID, '_post_note', TRUE); 
		if (!$post_note_meta_content) $post_note_meta_content = '';
		wp_nonce_field( 'post_note'.$post->ID, 'post_note_nonce');
		// Render editor meta box
		wp_editor( $post_note_meta_content, 'post_note', array('textarea_rows' => '5'));
	}

	add_action( 'save_post', 'post_note_meta_box_save' );
	function post_note_meta_box_save( $post_id )
	{
		// Bail if we're doing an auto save
		if( defined( 'DOING_AUTOSAVE' ) && DOING_AUTOSAVE ) return;
		 
		// if our nonce isn't there, or we can't verify it, bail
		if( !isset( $_POST['post_note_nonce'] ) || !wp_verify_nonce( $_POST['post_note_nonce'], 'post_note'.$post_id ) ) return;
		 
		// if our current user can't edit this post, bail
		if( !current_user_can( 'edit_post' ) ) return;
		
		
		// Make sure our data is set before trying to save it
		if( isset( $_POST['post_note'] ) )
			$result = update_post_meta( $post_id, '_post_note', $_POST['post_note'] );
	}
