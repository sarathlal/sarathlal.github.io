---
title: Write custom data to WordPress default debug.log file
layout: post
tags:
  - WordPress
---

The debugging WordPress code is so simple and WordPress have a nice debug systems to simplify the process as well as standardize code across the core, plugins and themes.

During theme & plugin development, I feel that the `debug.log` file was the most useful tool. It help me to sort out error in easier manner.

additionally, often I feel that I have to confirm the values of my objects, variables etc in my code during development. The `echo` & `var_dump()` are too useful. But in few situations, they are not enough.

Below you can find a handy function that help us to write our custom data in the WordPress `debug.log` file. Put the below code snippet in your theme's `functions.php` file or your custom plugin file.

	if (!function_exists('write_log')) {
		function write_log ( $log )  {
			if ( true === WP_DEBUG ) {
				if ( is_array( $log ) || is_object( $log ) ) {
					error_log( print_r( $log, true ) );
				} else {
					error_log( $log );
				}
			}
		}
	}


Then call the function with our variable in our code like below one.

	write_log($my_variable);

Check your `debug.log` file and if there is value in your variable, you can see that one.
