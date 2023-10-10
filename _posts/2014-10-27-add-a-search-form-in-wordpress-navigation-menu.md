---
title: Add a search form in WordPress navigation menu
author: sarathlal
layout: post
tags:
  - WordPress
---
To add a search form in WordPress navigation menu, we want to hook it into the `wp_nav_menu_items` filter as a menu item.

We just want to add few lines of code in our theme&#8217;s / child theme&#8217;s `functions.php` file.

    add_filter( 'wp_nav_menu_items','add_search_box', 10, 2 );
    function add_search_box( $items, $args ) {
     $items .= '<li>' . get_search_form( false ) . '</li>';
     return $items;
    }

This code snippet will add WordPress default search form in our navigation menu.

If we have multiple WordPress menus, we can specify the menu we want to add a search form in this function.

    add_filter( 'wp_nav_menu_items','add_search_box', 10, 2 );
    function add_search_box( $items, $args ) {
     if ( 'primary' == $args->theme_location )
     $items .= '<li>' . get_search_form( false ) . '</li>';
    
     return $items;
    }

Now the search form will only be displayed in the menu theme location named as primary.
