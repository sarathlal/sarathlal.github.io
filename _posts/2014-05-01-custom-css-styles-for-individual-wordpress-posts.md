---
title: Custom CSS styles for individual WordPress posts
author: sarathlal
layout: post
tags:
  - WordPress
---
In WordPress blogs, we use our theme&#8217;s `style.css` file to style our HTML elements. So in generally, WordPress blogs keep almost same layout & styles for all web pages.

We can easily add custom styles for each & every every WordPress pages because WordPress dynamically generate page or post wise container ( div element ) for each WordPress pages.

Have you ever tried to add custom styles for your page or post elements in WordPress?

We have different options to achieve this custom styling. Either we can add our custom styles in our child theme&#8217;s `style.css` file or we can use custom CSS plugins.

Instead of these two methods, we use a simple trick with custom fields to achieve this custom styling. I believe that you have a basic idea about custom fields in WordPress.

First add a few lines of code in our child theme&#8217;s `header.php` file.

	<?php if (is_single()) {
	$customstyle = get_post_meta($post->ID, 'customstyle', true);
		if (!empty($customstyle)) { ?>
			<style type="text/css">
			<?php echo $customstyle; ?>
			<style>
		<?php }
	} ?>

Using this simple code snippet, we retrieve the value of a custom field named as `customstyle` in our header as a style for single posts.

Once we add this code snippet, then we can add a custom field with the name `customstyle` and add the CSS codes in there as the value.

For example, if we want a border on certain image , we can add values on `customstyle` custom field like below.

	#myimageclass{border: 2px solid #ccc;}

Try this quick modification and make our WordPress pages as more beautiful.
