---
title: Hide / Disable WordPress admin bar
author: sarathlal
layout: post
tags:
  - WordPress
---
The WordPress automatically generate a admin bar at the top of every pages for logged in users. This admin bar is really an annoyance to some of us in different situations.

Today we are going to hide this admin bar using some simple code snippets.

To hide admin bar completely from front end for all users, put the below code snippet in theme&#8217;s / child theme&#8217;s `functions.php` file.

    add_action('after_setup_theme', 'remove_admin_bar');
    
    function remove_admin_bar() {
    show_admin_bar( false );
    }

We can hide admin bar for selected users only by adding an if statement with above lines of of code.

    add_action('after_setup_theme', 'remove_admin_bar');
    
    function remove_admin_bar() {
    if (!current_user_can('administrator') && !is_admin()) {
    show_admin_bar( false );
    }
    }

Now the admin bar is only visible for administrators.

Also we can use WordPress filter hook to hide this admin bar.

    add_action('after_setup_theme', 'remove_admin_bar');
    
    function remove_admin_bar() {
    add_filter('show_admin_bar', '__return_false');
    }
