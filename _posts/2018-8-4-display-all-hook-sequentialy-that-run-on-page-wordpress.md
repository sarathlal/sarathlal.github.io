---
title: Display all hooks sequentialy that run on a page - WordPress
layout: post
tags:
  - WordPress
---

Debugging WordPress code is an interesting job. If the issue is too complicated, finding the cause is an awesome activity.

As a technical support in a development company, often I have to face such issue. Our clients always will come with some interesting bugs. Almost, the cause is not from our plugin or theme. But we have responsibility to find out the cause.

In such situations, getting an idea about all hooks that run on that WordPress page helped me a lot. Below you can find the function that I'm using for debugging.

	add_action( 'all', 'th_show_all_hooks' );
		
	function th_show_all_hooks( $tag ) {
		if(!(is_admin())){ // Display Hooks in front end pages only
			$debug_tags = array();
			global $debug_tags;
			if ( in_array( $tag, $debug_tags ) ) {
				return;
			}
			echo "<pre>" . $tag . "</pre>";
			$debug_tags[] = $tag;
		}
	}
	
You can use above code in your theme's `functions.php` file or in your custom plugin file. Now this code only display hooks in front end pages. To track hooks in backend, just update the conditional tag.

Note: This  function only works in server with PHP 5.3+ versions and a global variable is used (It consider as bad practice).
