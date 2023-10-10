---
title: Display WordPress post and page ID in admin interface
author: sarathlal
layout: post
tags:
  - WordPress
---
In WordPress admin interface, when viewing all posts or pages as a list, WordPress offer few display options. We can hide and display some of the attributes and taxonomies of our pages and posts on this list.

In default, WordPress don&#8217;t have an option to display page ID or post ID on this list. But getting these ID numbers is useful when using plugins, widgets or theme options that require you to input specific IDs.

So to display the ID numbers, now we are going to add a small code snippet in our theme&#8217;s / child theme&#8217;s function.php file.

    add_filter('manage_posts_columns', 'posts_columns_id', 5);
     add_action('manage_posts_custom_column', 'posts_custom_id_columns', 5, 2);
     add_filter('manage_pages_columns', 'posts_columns_id', 5);
     add_action('manage_pages_custom_column', 'posts_custom_id_columns', 5, 2);
    function posts_columns_id($defaults){
     $defaults['wps_post_id'] = __('ID');
     return $defaults;
    }
    function posts_custom_id_columns($column_name, $id){
     if($column_name === 'wps_post_id'){
     echo $id;
     }
    }
    

Then save the file and navigate to Dashboard > Posts or > Pages to see the new column that display our page or post ID numbers.
