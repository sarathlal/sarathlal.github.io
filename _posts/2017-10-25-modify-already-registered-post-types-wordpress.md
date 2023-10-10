---
title: Modify already registered post types - WordPress
layout: post
tags:
  - WordPress
---

In a recent WordPress project, I need to modify the menu label of an already registered post type. The post type was registered by a plugin & I need regular updates of that plugin. So I can't edit the plugin.

Same situation happens before. Nowadays, too many premium plugins & themes will register various post types for the functionality. But client will argue that he need the perfect names in his dashboard.

After a quick search, I get an awesome WordPress function to modify already registered post type. You have to update below code snippet as per your post type.

	add_action( 'registered_post_type', 'xaxo_post_type_tweak', 10, 2 );
	/**
	 * @param string $post_type Registered post type name. 
	 * @param array $args Array of post type parameters.
	 */
	function xaxo_post_type_tweak( $post_type, $args ) {
		if ( 'your_posttype' === $post_type ) {
			global $wp_post_types;
			$args->labels->menu_name = __( 'New Menu Name', 'your_posttype' );
			$wp_post_types[ $post_type ] = $args;
		}
	}

