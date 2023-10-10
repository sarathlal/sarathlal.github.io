---
title: Custom post type with Post ID as slug for single post - WordPress 
layout: post
tags:
  - WordPress
---

In one of my recent project, our client need unique URL for single posts in a custom post type.

normally I prefer Post Title as slug and it always improve our SEO. We can achieve this SEO friendly URL from the permalink settings. But same time, I need Post ID as slug for single post in one custom post type only.

Each post in WordPress have a post ID and it is always unique one. So we can use this ID as an unique slug.

To do so, we have to use filter function for `post_type_link` filter hook and our custom rewrite rule. Please check the below code snippet. You have to edit the code snippet according to your post type.

####  1) Register post type

	function create_post_type_mycustomname() {
		$args = array(
			'capability_type' => 'post',
			'has_archive' => 'mycustomname',
			'rewrite' => array(
				'slug' => '/mycustomname',
				'feeds' => false
			)
		);

		register_post_type('ctp_mycustomname', $args);
	}
	add_action('init', 'create_post_type_mycustomname');

####  2) Change the links

	function mycustomname_links($post_link, $post = 0) {
		if($post->post_type === 'ctp_mycustomname') {
			return home_url('mycustomname/' . $post->ID . '/');
		}
		else{
			return $post_link;
		}
	}
	add_filter('post_type_link', 'mycustomname_links', 1, 3);

####  3) Add rewrites rules

	function mycustomname_rewrites_init(){
		add_rewrite_rule('mycustomname/([0-9]+)?$', 'index.php?post_type=ctp_mycustomname&p=$matches[1]', 'top');
	}
	add_action('init', 'mycustomname_rewrites_init');
