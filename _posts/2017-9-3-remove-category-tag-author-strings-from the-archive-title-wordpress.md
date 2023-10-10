---
title: Remove "Category:", "Tag:", "Author:" etc strings from the_archive_title - WordPress
layout: post
tags:
  - WordPress
---

In default, if we call `the_archive_title` function in a taxonomy archive page like category page, the page will display title as "Category: Your Category Name". We can see same type result in all other archive pages.

But in one of our recent WordPress project, client ask to remove the prefixes like, “Category:”, “Tag:”, “Author:”, etc from archive titles. Below, you can find a small code snippet that will do this job.

	function twem_custom_archive_title( $title ) {
		// Remove any HTML, words, digits, and spaces before the title.
		return preg_replace( '#^[\w\d\s]+:\s*#', '', strip_tags( $title ) );
	}
	add_filter( 'get_the_archive_title', 'twem_custom_archive_title' );
