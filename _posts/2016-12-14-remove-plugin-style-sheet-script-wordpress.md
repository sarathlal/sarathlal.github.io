---
title:  Remove Plugin Stylesheets and Scripts - WordPress
layout: post
tags:
  - WordPress
  - Page Optimization
---

Many WordPress plugins implicitly inject style sheets and JavaScript files into the page. If our theme is a customized one, we can eliminate some of these additional styles & scripts.

When you plan to optimize your WordPress site, you can find that these additional file request have some impact on our page load. So if possible, I suggest to optimize these additional file requests.

When scripts and styles are added properly, they use the `wp_enqueue_style` and `wp_enqueue_script` functions within the plugin files as such:

	// Styles Format:  wp_enqueue_style($handle, $src, $deps, $ver, $media);
	wp_register_style('pagination-style', plugins_url('style.css', __FILE__));
	wp_enqueue_style('pagination-style');

	// Script Format:  wp_enqueue_script($handle, $src, $deps, $ver, $in_footer);
	wp_register_script('jquery', 'http://ajax.googleapis.com/ajax/libs/jquery/1.7.2/jquery.min.js');
	wp_enqueue_script('jquery');

Those handle names are incredibly important because in our theme's `functions.php` we have to add their counterpart calls of `wp_dequeue_style` and `wp_dequeue_script` functions:

	// Remove from my page!
	wp_dequeue_style('pagination-style');
	wp_dequeue_script('jquery');

To remove plugin style sheets and scripts, we have to dig into the plugin code to find their script and style handles. But at the end, it will be worth.
