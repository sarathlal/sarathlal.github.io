---
title: Disable single page view & archive page view of Custom Post Type - WordPress
layout: post
tags:
  - WordPress
---

As a WordPress developer, often I have to use Custom Post Types in my plugins & theme.

I believe that you already have an idea about Custom Post Types. The Custom Post Type functionality help us to create & display custom type content in simple steps.

In most situations, I don't need a single page view / archive view for my custom post type. But I didn't care about that pages untill last time I noticed that these unnecessary pages are indexed in search engine results & it start to ruin my SEO ranking.

So now I believe that hiding unnecessary pages is an important act.

### Disable single page view & archive page view

If you don't need both, it is better to optimize our custom post type registration code.

	register_post_type('sample_post_type',array(
	'labels' => array(
		'name' => _x('Sample Posts', 'post type general name'),
		'singular_name' => _x('Sample Post', 'post type singular name')
	),
	'public' => true,
	'exclude_from_search' => true,
	'show_in_admin_bar'   => false,
	'show_in_nav_menus'   => false,
	'publicly_queryable'  => false,
	'query_var'           => false
	));

The `publicly_queryable` argument & its `false` value will hide all single pages & archive pages of this post type.

### Disable single page view & Show archive pages

	add_action( 'template_redirect', 'wpse_45164_redirect_press' );
	function wpse_45164_redirect_press()
	{
		if ( ! is_singular( 'press' ) )
			return;

		wp_redirect( get_post_type_archive_link( 'press' ), 301 );
		exit;
	}

The above code will redirect all single page view of `press` post type in to its post type archive page.
