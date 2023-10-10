---
title:  Delete meta values for all posts - WordPress
layout: post
tags:
  - WordPress
---

To delete post meta, the WordPress have `delete_post_meta()` function. We have to specify the `meta key` and `post id` as an argument for this function.

In some situations, we have to delete meta values of all posts.

Consider that we are going to create a plugin that will store some values as meta values for WordPress posts. In such situation, when user deactivate that plugin, it is better to remove this meta values for all posts.

	$to_del = array('meta_key_1', 'meta_key_2', 'meta_key_3');

	$args = array(
	  'post_type' => 'page',
	  'posts_per_page' => -1,
	  'ignore_sticky_posts' => true,
	  'fields' => 'ids',
	  'no_found_rows' => true
	);
	$q = new WP_Query($args);

	if (!empty($q->posts)) {
	  foreach ($q->posts as $pid) {
		foreach ($to_del as $d) {
		  delete_post_meta($pid,$d);
		}
	  }
	}
