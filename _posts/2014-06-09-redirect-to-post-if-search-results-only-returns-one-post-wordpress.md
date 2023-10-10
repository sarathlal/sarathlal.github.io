---
title: Redirect to post if search results only returns one post – WordPress
author: sarathlal
layout: post
tags:
  - WordPress
---
When we doing search in WordPress, it return list of all posts with in an archive template. The user can then click on the article they want to read.

If there is only one result for search, the result page is not necessary. In such conditions, simply redirecting the visitor directly to the article is make more sense.

Using a simple snippet, we can achieve this feature. Just add below function in our child theme&rsquo;s `function.php` file.

	add_action('template_redirect', 'redirect_single_post');

	function redirect_single_post() {
		if (is_search()) {
		global $wp_query;
		if ($wp_query->post_count == 1 && $wp_query->max_num_pages == 1) {
			wp_redirect( get_permalink( $wp_query->posts['0']->ID ) );
			exit;
		}
		}
	}
