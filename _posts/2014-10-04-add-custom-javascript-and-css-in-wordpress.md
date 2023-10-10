---
title: Add custom Javascript and CSS in WordPress
author: sarathlal
layout: post
tags:
  - WordPress
---
To add scripts and styles in Web pages, normally we just call them in header or footer. But WordPres have a proper & standard way to add scipt and styles in its header & footer.

###  Enqueue scripts in WordPress

The term Enqueue script means adding new script in WordPress using `wp_enqueue_script()` function.

The main WordPress functions that allow us to add scripts to WordPress are `wp_register_script` and `wp_enqueue_script`.

First we want to register our script using `wp_register_script()` function.

    wp_register_script( $id, $path, $dependencies, $version, $in_footer );

1.  id – whatever you like, best to be similar to the script – compulsory
2.  path – where the script is stored – compulsory
3.  dependencies – what other scripts if any are required – optional
4.  version – you can name this whatever you like, best to name it what the version actually is – optional – defaults to WordPress version number
5.  header or footer location – true for footer, false for header – optional – defaults to header

After register the script, we still want to enqueue it. Enqueuing tells WordPress to actually place any previously registered Script or Stylesheet on the page.

    wp_enqueue_script($id);

####  example

	<?php
	function new_custom_plugin_scripts() {
	 wp_register_script('my_amazing_script', plugins_url('amazing_script.js', __FILE__), array('jquery'),'1.1', true);//Register script from plugin folder
	 wp_enqueue_script('my_amazing_script');
	} 
	add_action( 'wp_enqueue_scripts', 'new_custom_plugin_scripts' );

	function new_custom_theme_scripts() {
	 wp_register_script ('placeholder', get_stylesheet_directory_uri() . '/js/placeholder.js', array( 'jquery' ),'1',true);//Register script from theme folder
	 wp_enqueue_script('placeholder');
	}
	add_action( 'wp_enqueue_scripts', 'new_custom_theme_scripts' );
	?>

###  Enqueue styles in WordPress

To add custom styles in WordPress, we have another two API functions. They are `wp_register_style` and `wp_enqueue_style`.

Same like scripts, first we want to register styles with WordPress.

    wp_register_style( $id, $path, $dependencies, $version, $media );

The `wp_register_style()` function takes similar arguments for id, path, dependencies and version.

The last argument is the media device type that the stylesheet applies to. This defaults to all. It can take values like screen or print.

For themes the Path parameter has 2 variations. They depend on whether you want Child themes to be able to override our scripts and styles.

To allow child themes to override the style, we want to use`get_stylesheet_directory_uri`.

    get_stylesheet_directory_uri() . '/css/my-style.css';

And to prevent the style being overridden, then we want to use `get_template_directory_uri`,

    get_template_directory_uri() . '/css/my-style.css';

After register the style, then we want to enqueue it.

    wp_enqueue_style($id);

####  Example

	<?php
	function new_custom_plugin_styles() {
	 wp_register_script('my_amazing_style', plugins_url('amazing_style.css', __FILE__), array(''), '1.1', 'all' );//Register style from plugin folder
	 wp_enqueue_script('my_amazing_style');
	} 
	add_action( 'wp_enqueue_scripts', 'new_custom_plugin_styles' );

	function new_custom_theme_styles() {
	 wp_register_script ('placeholder', get_stylesheet_directory_uri() . '/css/placeholder.css', array( '' ), '1','all');//Register style from theme folder
	 wp_enqueue_script('placeholder');
	}
	add_action( 'wp_enqueue_scripts', 'new_custom_theme_styles' );

	?>
