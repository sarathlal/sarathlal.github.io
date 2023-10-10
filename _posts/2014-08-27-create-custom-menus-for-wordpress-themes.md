---
title: Create custom menus for WordPress themes
author: sarathlal
layout: post
tags:
  - WordPress
---
We can easily make & use new custom menus in our WordPress themes. Now I just walk through on different stages in this process.

First we want to register our new menu in our theme&#8217;s `functions.php` file.

	function register_my_menu() {
	 register_nav_menu('my-menu',__( 'My Menu' ));
	}
	add_action( 'init', 'register_my_menu' );

Then to display this menu, we want to tell the theme where we like the menus to show up. It may be any template file like `header.php`, `footer.php` etc according to our design.

So just add a line of code in appropriate file to show this new menu in our pages.

	<?php wp_nav_menu( array( 'theme_location' => 'my-menu' ) ); ?>
	
If you like some wrapper for our new menu, just add an additional array element with this WordPress function.

<?php wp_nav_menu( array( 'theme_location' => 'my-menu', 'container_class' => 'my_extra_menu_class' ) ); ?>

Now our new menu is wrapped within a container with a class named as my\_extra\_menu_class.

Same way, making multiple custom menus is also too simple.

	function register_my_menus() {
	 register_nav_menus(
	 array(
	 'header-menu' => __( 'Header Menu' ),
	 'extra-menu' => __( 'Extra Menu' )
	 )
	 );
	}
	add_action( 'init', 'register_my_menus' );
