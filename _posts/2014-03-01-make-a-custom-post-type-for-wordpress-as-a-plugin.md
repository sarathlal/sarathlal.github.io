---
title: Make a custom post type for WordPress as a plugin
author: sarathlal
layout: post
tags:
  - WordPress
---
In default, WordPress have 5 post type & they are known as Posts, Pages, Attachment, Revision & Navigation menu. Additional to this post types, we can make our own post types & they are known as Custom Post Types in WordPress.

I always like to make my Custom Post Type as a plugin to keep it independent with themes. Else when we switch to another theme, we want to code again for our Coustom Post Type content.

###  step1: Make a folder for our Custom Post Type in our plugin directory

Open WordPress plugin directory, make a new folder inside it & name it as Book Reviews.

###  Step2: Make essential files for our plugin

Inside Book Reviews plugin folder, make a new php file & name it as `book_reviews.php`.

###  Step3: Make it as a php file

To make it as a php file, just insert an opening PHP tag, `<?php` at top.

###  Step4: Give a name to our plugin

Now we want to give essential header text for our plugin like name, author name, version, plugin URL etc. So write down your credential like below.
    
	/*
	Plugin Name: Book Reviews
	Description: Declares a plugin that will create a custom post type displaying book reviews.
	Version: 1.0
	Author: Your Name
	Author URI: http://yourdomain.com/
	License: GPLv2
	*/

###  Step5: Initialize function for our Custom Post Type

Now we want to add an action when the WP Admin initialize to call the function that generate our Book Reviews. So copy & paste below code in to our php file.
    
	add_action( 'init', 'cpt_book_review', 0 );

###  Step6: Make our function & register it as a custom post type

Now we want to make & register our function `cpt_book_review()` with labels and argument related with our Book Reviews Custom Post Type.
    
	// Register Custom Post Type
	function cpt_book_review() {

		$labels = array(
			'name'                => _x( 'Book Reviews', 'Post Type General Name', 'text_domain' ),
			'singular_name'       => _x( 'Book Review', 'Post Type Singular Name', 'text_domain' ),
			'menu_name'           => __( 'Book Reviews', 'text_domain' ),
			'parent_item_colon'   => __( 'Parent Book Review:', 'text_domain' ),
			'all_items'           => __( 'All Book Review', 'text_domain' ),
			'view_item'           => __( 'View Book Review', 'text_domain' ),
			'add_new_item'        => __( 'Add New Book Review', 'text_domain' ),
			'add_new'             => __( 'Add New', 'text_domain' ),
			'edit_item'           => __( 'Edit Book Review', 'text_domain' ),
			'update_item'         => __( 'Update Book Review', 'text_domain' ),
			'search_items'        => __( 'Search Book Review', 'text_domain' ),
			'not_found'           => __( 'Not found', 'text_domain' ),
			'not_found_in_trash'  => __( 'Not found in Trash', 'text_domain' ),
		);
		$rewrite = array(
			'slug'                => 'book-review',
			'with_front'          => true,
			'pages'               => true,
			'feeds'               => true,
		);
		$args = array(
			'label'               => __( 'book-review', 'text_domain' ),
			'description'         => __( 'Book Reviews information', 'text_domain' ),
			'labels'              => $labels,
			'supports'            => array( 'title', 'editor', 'excerpt', 'thumbnail', 'comments', 'custom-fields', 'page-attributes', ),
			'taxonomies'          => array( 'category', 'post_tag' ),
			'hierarchical'        => false,
			'public'              => true,
			'show_ui'             => true,
			'show_in_menu'        => true,
			'show_in_nav_menus'   => true,
			'show_in_admin_bar'   => true,
			'menu_position'       => 5,
			'can_export'          => true,
			'has_archive'         => true,
			'exclude_from_search' => false,
			'publicly_queryable'  => true,
			'rewrite'             => $rewrite,
			'capability_type'     => 'page',
		);
		register_post_type( 'cpt_book_review', $args );
	}

If you like to know more about arguments & labels used on this array, please visit [this link][1].

###  Step7: Save & Activate our plugin

*   Just save our php file & then activate our Book Reviews plugin from admin back end of WordPress.

###  Step8: Add new book reviews

*   Same like posts, now we can add book reviews, categorize & tag them.

 [1]: http://codex.wordpress.org/Function_Reference/register_post_type
