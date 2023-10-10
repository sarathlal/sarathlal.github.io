---
title: Get blog page URL - WordPress
layout: post
tags:
  - WordPress
---

In default, WordPress display its latest posts in home page. As we know, WordPress have option to display its posts on a separate static page from reading settings.

In some situations, I need to use this static blog page URL in my template files. Below you can find a small function, that will return the blog page URL.

	function get_blog_posts_page_url() {
		// If front page is set to display a static page, get the URL of the posts page.
		if ( 'page' === get_option( 'show_on_front' ) ) {
			return get_permalink( get_option( 'page_for_posts' ) );
		}
		// The front page is the posts page. Get its URL.
		return get_home_url();
	}

We have to use `get_blog_posts_page_url()` in our template files to get blog page URL.
