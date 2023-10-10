---
title: Add custom style sheet on new post or edit post admin pages - WordPress
layout: post
tags:
  - WordPress
---

In one of my recent WordPress customisation, I want to add custom style sheet on  new post and edit post admin pages.

To do so, we can use below code snippet in our theme functions file or plugin functions file.

	/**
	 * is_edit_page 
	 * function to check if the current page is a post edit page
	 */
	function is_edit_page($new_edit = null){
		global $pagenow;
		//make sure we are on the backend
		if (!is_admin()) return false;

		if($new_edit == "edit")
			return in_array( $pagenow, array( 'post.php',  ) );
		elseif($new_edit == "new") //check for new post page
			return in_array( $pagenow, array( 'post-new.php' ) );
		else //check for either new or edit
			return in_array( $pagenow, array( 'post.php', 'post-new.php' ) );
	}

	/**
	 * Adds the meta box stylesheet when appropriate
	 */
	function add_metabox_admin_style( $hook ) {
	   if (is_edit_page()){ 
			wp_enqueue_style( 'prfx_meta_box_styles', get_template_directory_uri() . '/css/meta-box-styles.css' );
	   }
	}
	add_action( 'admin_print_styles', 'add_metabox_admin_style', 10, 1 );


If you plan to add style sheet from theme, use the code as it is. If you have to add style sheet from custom plugin, use `plugin_dir_url( __FILE__ )` instead of `get_template_directory_uri()` that will return current plugin URL.
