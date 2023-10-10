---
title: Make custom taxonomies for WordPress as a plugin
author: sarathlal
layout: post
tags:
  - WordPress
---
The taxonomies are way to group posts & pages in WordPress. In WordPress, to group our contents, we normally use categories & tags. They are two important & default taxonomies in WordPress. Same like categories & tags, we can make our own taxonomies in WordPress. They are known as custom taxonomies.

For example, consider a news site, we can categorize news & we can assign tags for them. If there is a possibility to group news in a location wise, it will improve usability of our website.

Like such situations, we can make our own taxonomies like location & we can group our content with new taxonomies. Today I share a code snippet to make custom taxonomy, &#8220;Location&#8221; for WordPress Posts.

To make my custom taxonomies as a theme independent, I like to make it as a plugin.

First, we want to make a folder inside WordPress plugin directory for our custom taxonomy plugin. Then make a php file inside it & paste below code in to it.

    <?php
    /*
    Plugin Name: Location Taxonomies
    Description: Declares a plugin that will create a custom taxonomy "Location" to group posts.
    Version: 1.0
    Author: Your Name
    Author URI: http://yourdomain.com/
    License: GPLv2
    */

    function add_location_custom_taxonomies() {
        // Add new "Locations" taxonomy to Posts
        register_taxonomy('location', 'post', array(
            // Hierarchical taxonomy (like categories)
            'hierarchical' => true,
            // This array of options controls the labels displayed in the WordPress Admin UI
            'labels' => array(
                'name' => _x( 'Locations', 'taxonomy general name' ),
                'singular_name' => _x( 'Location', 'taxonomy singular name' ),
                'search_items' =>  __( 'Search Locations' ),
                'all_items' => __( 'All Locations' ),
                'parent_item' => __( 'Parent Location' ),
                'parent_item_colon' => __( 'Parent Location:' ),
                'edit_item' => __( 'Edit Location' ),
                'update_item' => __( 'Update Location' ),
                'add_new_item' => __( 'Add New Location' ),
                'new_item_name' => __( 'New Location Name' ),
                'menu_name' => __( 'Locations' ),
            ),
            // Control the slugs used for this taxonomy
            'rewrite' => array(
                'slug' => 'locations', // This controls the base slug that will display before each term
                'with_front' => false, // Don't display the category base before "/locations/"
                'hierarchical' => true // This will allow URL's like "/locations/boston/cambridge/"
            ),
        ));
    }
    add_action( 'init', 'add_location_custom_taxonomies', 0 );

Inside this code snippet, the first part is the information about our plugin. Here we name it, give a brief description & give essential credits to plugin author.

Then we make a function to create `location` taxonomy & register it as a taxonomy.

Just save that PHP file & then activate our new plugin in WordPress admin end. A new &ldquo;Locations&rdquo; box will appear to the right of our posts in the WordPress admin area. We can use this the way like categories.
