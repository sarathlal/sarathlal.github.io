---
title: Display categories as drop down list in WordPress template file
author: sarathlal
layout: post
tags:
  - WordPress
---
When doing WordPress customizations, often I required drop down list of all category if I have a large number of category in my blogs.

This drop down list can save a large area in our themes. We just want to paste a small code snippet on our template file.

	<form action="<?php bloginfo('url'); ?>/" method="get">
	<?php
		$select = wp_dropdown_categories('show_option_none=Select Category&show_count=1&orderby=name&echo=0&selected=6');
		$select = preg_replace("#<select([^>]*)>#", "<select$1 onchange='return this.form.submit()'>", $select);
		echo $select;
		?>
	<noscript><input type="submit" value="View" /></noscript>
	</form>

In this code snippet, we use `wp_dropdown_categories` function to retrieve all category as a drop down list. If you like more customization on this function, visit [function referance page][1] in WordPress codex.

 [1]: http://codex.wordpress.org/Function_Reference/wp_dropdown_categories
