---
title: Use first Post image as featured image in WordPress
author: sarathlal
layout: post
tags:
  - WordPress
---
The WordPress have a featured image option for posts. If we have an introduction image for our post, we can make it as a featured image & can display it in our pages.

Beginning with an image is a good idea. If the image can speak well, we can catch the readers. But we know that getting a good featured image is little hard for normal users.

In almost blog, we will use few images with in posts. If we are not too bothered about dedicated featured image, we can use the first post image as featured image for posts and pages.

We use a simple function to achieve this hack. The function uses the global variable `$post` to parse the post&rsquo;s content with a regular expression. If an image is found, its URL is returned by the function. If not, the default image URL is returned.

*   First we want to open the `functions.php` file in our theme.
*   Paste this code in it. Don&rsquo;t forget to specify a default image on line 10 & add an image in image sub folder (in case a post of ours does not have an image).

		function catch_that_image() {
			global $post, $posts;
			$first_img = '';
			ob_start();
			ob_end_clean();
			$output = preg_match_all('/<img.+src=['"]([^'"]+)['"].*>/i', $post->post_content, $matches);
			$first_img = $matches [1] [0];

			if(empty($first_img)){ //Defines a default image
				$first_img = "/images/default.jpg";
			}
				return $first_img;
		}

*   Save the functions.php file.

*   On your blog home page (index.php etc), call this function to get the URL of the first image from the post.
    
		<?php echo catch_that_image() ?>

I think this trick is helpful for personnel bloggers & beginners. Try this one & start our post with an image.
