---
title:  Remove query string from static resources ( CSS & Javascript ) - WordPress
layout: post
tags:
  - WordPress
  - Page Optimization
---

When we test our WordPress pages on tools like Pingdom, GTmatrix, Google Page Speed Insights or YSlow, we will get a warning to remove query strings from static resources.

In WordPress, when we includes a script or a stylesheet by using the `wp_enqueue_style` or `wp_enqueue_script` functions, it will include a query string for the version of the file in file request.

Both of these functions have a version parameter which allows the developer to append any version number as the query string. Also if the version number doesn't exist in the function, then WordPress will append the WordPress version to the end of the URLs.

The reason why WordPress adds a version number to the end of the URLs is for cache updates. Once WordPress is updated to a new version, then this new version number will be added to the end of the URL. If any of the JavaScript or stylesheet files have changed on this update, then the new version number will ensure that the browser fetches the latest version and not the version stored in the browser cache.

But this query string will reduce our page speed and so the above listed tools suggest to remove query strings from static resources.

So to remove query string from static resources enqueued by `wp_enqueue_style` or `wp_enqueue_script` functions, pass a NULL value on the version parameter for both functions.

	wp_enqueue_script( $handle, $src, $deps, $version, $in_footer );
	wp_enqueue_style( $handle, $src, $deps, $version, $media );
	
But still there is chance for styles & scripts on a WordPress site that we haven't any control (for example, styles and scripts enqueued by plugins).

So to remove query string from those CSS & Javascript file request, we are going to use WordPress filter hook `script_loader_src`.

We want to add below code snippet in our theme's `functions.php` file.

	function sart_remove_script_version( $src ){
		return remove_query_arg( 'ver', $src );
	}

	add_filter( 'script_loader_src', 'sart_remove_script_version' );
	add_filter( 'style_loader_src', 'sart_remove_script_version' );

Save the file and then check the web page again. We can understand the difference.

Removing those query strings will ensure that the proxy can cache those resources and it will speed up the loading time of our website.

###  If you are using W3 Total Cache,

Go to Browser Cache tool tab and find "Prevent caching of objects after settings change" option in "General Settings" . Uncheck it and don’t forget to save settings. Now "Empty all Cache" and you are done.
