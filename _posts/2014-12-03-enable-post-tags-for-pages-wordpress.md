---
title: Enable post tags for pages -WordPress
author: sarathlal
layout: post
tags:
  - WordPress
---

In default, the post tag taxonomy is only enabled in WordPress posts.

To enable post tags for WordPress pages, just add below code snippet in to your theme’s / child theme’s `function.php` file.

	// add tag support to pages
	function tags_support_all() {
	 register_taxonomy_for_object_type('post_tag', 'page');
	}

	// ensure all tags are included in queries
	function tags_support_query($wp_query) {
	 if ($wp_query->get('tag')) $wp_query->set('post_type', 'any');
	}

	// tag hooks
	add_action('init', 'tags_support_all');
	add_action('pre_get_posts', 'tags_support_query');

If you have further custom post types which require tags, you’ll need to add `register_taxonomy_for_object_type` calls for each post types with second argument as our post type name.
