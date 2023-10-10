---
title:  Remove color scheme picker from WordPress profile page
layout: post
tags:
  - WordPress
---

![WordPress color scheme picker in profile page](/images/2017/profile-page-color-scheme-picker-wordpress.png)

	//Remove color scheme picker from WordPress profile page
	remove_action( 'admin_color_scheme_picker', 'admin_color_scheme_picker' );
