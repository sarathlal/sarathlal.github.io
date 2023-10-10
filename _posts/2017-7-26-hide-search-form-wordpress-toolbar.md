---
title:  Hide search form in WordPress toolbar
layout: post
tags:
  - WordPress
---

![Hide search form in WordPress toolbar](/images/2017/wordpress-toolbar-search-form.png)


	//Hide search form in WordPress toolbar
	function hide_admin_bar_search () {
		echo '<style type="text/css">
		#adminbarsearch {
			display: none;
		}
		</style>';
	}
	add_action('admin_head', 'hide_admin_bar_search');
	add_action('wp_head', 'hide_admin_bar_search');
