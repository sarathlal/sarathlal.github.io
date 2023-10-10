---
title: Determine the status of a script - WordPress
layout: post
tags:
  - WordPress
---

When making new plugin or customizing WordPress themes in deep, we want to check that if a script has been registered, enqueued, printed, or is waiting to be printed.

This method is very useful to avoid conflicts between scripts during registering/enqueing scripts in our plugins and themes.

The WordPress have a default function to check the status of script.

	wp_script_is( $handle, $list );
	
### Parameters

* $handle :- Name of the script (string & required).

Default value: None

* $list :- The list to query (string & optional).

	1. `registered` - script was registered through wp_register_script()
	2. `enqueued` / `queue` - script was enqueued
	3. `done` - script has been printed
	4. `to_do` - script has not yet been printed

Default: enqueued

### Return Values

True or false.

### Example 1

	$handle = 'fluidVids.js';
	$list = 'enqueued';
	if (wp_script_is( $handle, $list )) {
		return;
	} else {
		wp_register_script( 'fluidVids.js', plugin_dir_url(__FILE__).'js/fluidvids.min.js');
		wp_enqueue_script( 'fluidVids.js' );
	}


### Example 2

On the below example, we are going to check that if jQuery is printed & if so, we will add a custom jQuery snippet to our footer from our theme's `functions.php`.
		
	function myscript() {
		if( wp_script_is( 'jquery', 'done' ) ) {
		?>
		<script type="text/javascript">
		  // script dependent on jQuery
		</script>
		<?php
		}
	}
	add_action( 'wp_footer', 'myscript' );

