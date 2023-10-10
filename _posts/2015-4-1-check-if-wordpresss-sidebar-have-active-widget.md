---
title: Check if WordPress sidebar have active widgets
layout: post
tags:
  - WordPress
---

In almost WordPress themes, they have sidebars on pages. In one of the recent WordPress customization, I want to hide side bar section if there aren’t any active widgets on it.

In WordPress, we have a function, `wp_get_sidebars_widgets()` to get all active widgets. We can use this function with in a custom function and by the way we can check that there is any active widget on particular widget area.

Just use below code snippet in our theme's or child them's `functions.php` file.

	function is_sidebar_active($index) {
		global $wp_registered_sidebars;
		$widgetcolums = wp_get_sidebars_widgets();
		if ($widgetcolums[$index])
			return true;
		return false;
	}

The below code snippet can checks if a sidebar (widget area) has any active widget on it. So use below code snippet in our page template that have sidebars.

	if( is_sidebar_active( 'sidebar-name' ) ):
	// Our sidebar comes here
	endif;
