---
title:  Remove page title using filter - WordPress
layout: post
tags:
  - WordPress
---

In some situations, I have to remove / hide WordPress page titles for specific pages.

There is too many options to hide or remove page titles.

1. Hide page titles using CSS
2. Use conditional statements in template files
3. Use filter hook

I most prefer the last option (Use filter hook) to remove the page titles because it is simple and the clean one.

We have to add a small code snippet in our theme's `functions.php` file.

	//Remove page title from my account page
	add_filter( 'the_title', 'remove_page_title', 10, 2 );
	function remove_page_title( $title, $id ) {
		$hide_title_page_ids = array(7,17,53);//Page IDs
		foreach($hide_title_page_ids as $page_id) {
			if( $page_id == $id ) return '';
		}
		return $title;
	}
	
