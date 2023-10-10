---
title: Change number of posts displayed per page as per conditions - WordPress
layout: post
tags:
  - WordPress
---

In WordPress reading settings, there is an option to set the number of post displayed per page.

![WordPress color scheme picker in profile page](/images/2017/number-of-post-displayed-wordpress-reading-settings.png)

In all archive pages including blog, taxonomy and search archives etc, number of posts per page is displayed as per this count. Also a pagination will be displayed at the bottom of the page as per this count.

But in some specific situation, I need to change this number in various archive pages.

Consider that you have new custom post type called gallery. In default blog page, I have to display my most recent 10 blog posts with a pagination. Same time, I need to display 12 gallery post in the main gallery archive page.

In such situation, we can use WordPress `pre_get_posts()` function to tweak the WordPress query.

Below, you can find the code snippet that achive the above requirement. You have to update the conditional tags in the below code as per your requirement.

	/* Change number of post per page for gallery post type */
	function set_posts_per_page_for_gallery( $query ) {
	  if ( !is_admin() && $query->is_main_query() && is_post_type_archive( 'gallery' ) ) {
		$query->set( 'posts_per_page', '12' );
	  }
	}
	add_action( 'pre_get_posts', 'set_posts_per_page_for_gallery' );
