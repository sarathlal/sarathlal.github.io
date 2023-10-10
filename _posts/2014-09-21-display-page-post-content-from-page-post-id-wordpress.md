---
title: 'Display page ( post ) content from page ( post ) ID &#8211; WordPress'
author: sarathlal
layout: post
tags:
  - WordPress
---
To display WordPress page or post content from its ID, we can simply use get_post() function.

	<?php
	$id=14;
	$post = get_post($id);
	$title = apply_filters('the_title', $post->post_title);
	echo $title;
	$content = apply_filters('the_content', $post->post_content);
	echo $content;
	?>

Now we retrieved the content of page ( post ) with an ID of 14.
