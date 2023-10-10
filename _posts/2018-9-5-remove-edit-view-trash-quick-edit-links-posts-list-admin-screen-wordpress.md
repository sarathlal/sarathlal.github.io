---
title: Remove edit, view, trash and quick edit links within posts list of admin screen - WordPress
layout: post
tags:
  - WordPress
---

![Remove edit, view, trash and quick edit links - WordPress](/images/2018/edit-view-trash-quick-edit-links-posts-wordpress.png)

Use below code snippet to remove the edit, view, trash and quick edit links that we seen when we mouse over a post in the post list in admin screens.


	add_filter( 'post_row_actions', 'remove_row_actions', 10, 1 );

	function remove_row_actions( $actions ){
		// Confirm post type
		if( get_post_type() === 'post' ){
			unset( $actions['edit'] );
			unset( $actions['view'] );
			unset( $actions['trash'] );
			unset( $actions['inline hide-if-no-js'] );
		}    
		return $actions;
	}
