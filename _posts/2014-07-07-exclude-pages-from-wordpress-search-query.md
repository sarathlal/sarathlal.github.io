---
title: Exclude Pages from WordPress Search query
author: sarathlal
layout: post
tags:
  - WordPress
---
When we make blogs using WordPress, typically we have hundreds of blog posts & few pages. In WordPress, these pages & posts have different functionalists.

Generally we used pages to display important static information like about, contact etc. We always like to display our important pages in WordPress menu & side bar.

Normally I think, these pages don&rsquo;t have any roles in search result or they have low priority in search results. In certain conditions, we want to hide our special pages from normal visitors.

So using a simple code snippet, we are going to hide WordPress pages in search results.

Just add below function in our child theme&rsquo;s `function.php` file. Then after, our WordPress blog only display posts in search results.

	function filter_search($query) {
		if ($query->is_search) {
		$query->set('post_type', 'post');
		}
		return $query;
	}
	add_filter('pre_get_posts', 'filter_search');
