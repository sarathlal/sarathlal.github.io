---
title: 'Modify excerpt length &#038; more tag &#8211; WordPress'
author: sarathlal
layout: post
tags:
  - WordPress
---
In WordPress, it have ability to display automatically fetched excerpt for search result, index & archive pages. But in default, the excerpt length is limited with in 55 words.

If we like to modify this excerpt length, we can easily achieve this by adding a simple function & filter in our child theme&#8217;s `function.php` file.

	// Changing excerpt length
	function new_excerpt_length($length) {
	return 100;
	}
	add_filter('excerpt_length', 'new_excerpt_length');

From now, our excerpt length will be 100 words.

##  Modify more tag

At the end of each excerpt, WordPress display some more tag like `[...]` etc. We can also modify this more tag by another simple function & filter.

	// Changing excerpt more
	function new_excerpt_more($more) {
	return '<span class="continue-reading"> <a href="' . get_permalink() . '">Continue Reading »</a></span>';
	}
	add_filter('excerpt_more', 'new_excerpt_more');

We just want to copy & paste above code in to our child theme&#8217;s `function.php` file. Try this code & view the changes.
