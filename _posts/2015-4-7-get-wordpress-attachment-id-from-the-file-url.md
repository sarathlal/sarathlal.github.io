---
title: Get WordPress attachment ID from the file URL
layout: post
tags:
  - WordPress
---

When we uploaded images in WordPress, the WordPress generate multiple copies of that image in upload folder with different size like thumbnail, medium etc.

We can effectively use these images on our pages and by the way, we can optimize the use of images in our web pages.

But now I only have uploaded image URL because I'm used a plugin for some custom theme & page settings. That plugin only return the path of uploaded image URL.

If I have Attachement ID of that uploaded image, I know the WordPress function to get different image size of that image from attachment ID. So now I need a custom function to get attachment ID from uploaded image URL.

	// retrieves the attachment ID from the file URL
	function gyaxhz_get_image_id($image_url) {
		global $wpdb;
		$attachment = $wpdb->get_col($wpdb->prepare("SELECT ID FROM $wpdb->posts WHERE guid='%s';", $image_url )); 
			return $attachment[0]; 
	}

Just check below code snippet to understand how the above function can works on our theme.

	// set the image url
	$image_url = 'http://yourdomain.com/wp-content/uploads/2011/02/14/image_name.jpg';
	 
	// store the image ID in a var
	$image_id = gyaxhz_get_image_id($image_url);
	 
	// retrieve the thumbnail size of our image
	$image_thumb = wp_get_attachment_image_src($image_id, 'thumbnail');
	 
	// display the image
	echo $image_thumb[0];
