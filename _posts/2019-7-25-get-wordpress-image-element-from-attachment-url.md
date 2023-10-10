---
title: Get WordPress image element from attachment URL - WordPress
layout: post
tags:
  - WordPress
tested: WordPress 5.2
---


If we have an image URL, we can easily make it an HTML image tag. But when we deal with WordPress, it is always better to use WordPress functions to render an image element.

So now consider that we have an image URL.

### Step 1 - Get attachment ID from image URL

	$attachment_id = attachment_url_to_postid( 'http://example.com/wp-content/uploads/2019/05/castle-old.jpg' );

## Step 2 - Get image HTML tag from attachment ID

	wp_get_attachment_image ( $attachment_id, string|array $size = 'thumbnail', false, '' );
