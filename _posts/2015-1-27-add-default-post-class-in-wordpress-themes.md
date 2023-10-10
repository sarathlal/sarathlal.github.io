---
title: Add default post class in WordPress themes
author: sarathlal
layout: post
tags:
  - WordPress
---

When creating new themes for WordPress, often I want to apply different style for various post types, archives or pages. Makeing new templates is the better way to use different page layouts. But if we can reuse the same page layout with differnt styles for different pages, it is consider as a best pracices in WordPress theming.

To do so, WordPress have a function, `post_class()`. We just want to call this function in our page element.

	<div id="post-<?php the_ID(); ?>" <?php post_class(); ?>>

By adding this function on that div, some post specific css classes will be added to that element. We can use them to modify the looks of our WordPress posts via CSS. The following classes are added by default:

	.post-id
	.post
	.attachment
	.sticky
	.hentry (hAtom microformat pages)
	.category-ID
	.category-name
	.tag-name

example:

	<div id="post-4564" class="post post-4564 category-48 category-songs logged-in">

So from the above example, now we can apply different style for `category-songs` class & they will get entirly different styles than other categories.

	.category-songs {background: #97c3e1; border: 1px solid #84aac4;}

But if you need more controll, you can manually add some classes within that function.

	<?php post_class('class-1 class-2'); ?>

We can also modify this function to get PHP variable values with post class like below example.

	<?php $author = get_the_author_meta('display_name'); ?>

	<?php post_class('class-1 class-2 ' . $author); ?>

##### output

	<div id="post-4564" class="post post-4564 category-48 category-dancing logged-in class-1 class-2 author1">

This is an essential function we want to use in our WordPress themes and it will make our themes as too flexible for further modifications.
