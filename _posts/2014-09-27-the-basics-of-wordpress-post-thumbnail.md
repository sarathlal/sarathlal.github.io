---
title: The basics of WordPress post thumbnail
author: sarathlal
layout: post
tags:
  - WordPress
---
To dispaly post thumbnails in WordPress, we can use `the_post_thumbnail()` function.

In default, When we upload image, WordPress re size them in to different width and height & then upload these images in to upload folder. To access them, we want to add there default name as parameter in this `the_post_thumbnail()` function.

	the_post_thumbnail('thumbnail'); // Thumbnail (default 150px x 150px max)
	the_post_thumbnail('medium'); // Medium resolution (default 300px x 300px max)
	the_post_thumbnail('large'); // Large resolution (default 640px x 640px max)
	the_post_thumbnail('full'); // Original image resolution (unmodified)

If we still like some other dimensions for our post thumbnail, we can use these dimension as function parameter.

	the_post_thumbnail( array(200, 140) ); // 200px width & 140px height
