---
title: Update query order - WordPress
layout: post
tags:
  - WordPress
---

The WordPress post type archives are ordered by date, descending by default. This is the best & suitable listing method for a blogging platform.

In a recent project, I have to use WordPress default archive pages to list out posts in a custom post type. As per the default nature, the WordPress will list all posts in that custom post type as per the order of published date.  But client need to list posts based on post title in ascending order.

If the content chronology isn’t important, there is no sense for a date wise listing.

In such cases, we can reorder the posts using `pre_get_posts` filter hook. Also we can use conditional tag to specify the archives.

### Sort blog page listing by title

	add_action( 'pre_get_posts', 'foo_modify_query_order' );
	function foo_modify_query_order( $query ) {
		if ( $query->is_home() && $query->is_main_query() ) {
			$query->set( 'orderby', 'title' );
			$query->set( 'order', 'ASC' );
		}
	}

### Sort archive page listing by menu order

	add_action( 'pre_get_posts', 'bar_modify_query_order'); 
    function bar_modify_query_order($query){
        if(is_archive()) {
           $query->set( 'orderby', 'menu_order' );       
           $query->set( 'order', 'ASC' );
        }    
    };
