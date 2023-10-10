---
title: Show post excerpts in archives and index pages in WordPress
author: sarathlal
layout: post
tags:
  - WordPress
---

In default, Home and Archive pages in WordPress themes shows a recent list of posts with complete content. But almost people like to display only a list of post excerpt in Home and Archive pages.

Post excerpts are short notes about our posts for visitors. We can handcraft each post excerpt or can use beginning of post as excerpt in WordPress theme. The post excerpts reduces web page loading time and it help visitors to evaluate the full content and the subjects covered in that post.

Almost WordPress themes are capable to display automatically fetched post excerpt in certain conditions. In WordPress twenty twelve and twenty thirteen themes, it show automatically fetched post excerpt in search result using the content template.

If you are using Twenty Twelve or Twenty Thirteen themes, in line 33 of `content.php`, you can find a if statement.

	<?php if ( is_search() ) : // Only display Excerpts for Search ?>

Now we want to modify this if statement which shows post excerpt for search result.

*   First we want to open `content.php` file in child theme*.
*   Remove the above stated if statement ( In line 33 of twenty twelve or twenty thirteen theme ) with below code.

		<php if ( is_search() || is_home() || is_category() || is_tag() ) : // Display Excerpts for Search, Homepage, category and tag archives pages?>

*   Save `content.php` file in your child theme and reload your home page.

##  Replace [...] in excerpt with Continue Reading link

Now your home page shows automatically fetched post excerpt from our post with [...] at the end. We can easily remove this Excerpt more symbol [...] with a Continue Reading text link.

*   Open `functions.php` file in our child theme**.
*   Copy and paste below code snippet to `functions.php` file.

		// Remove the ... from excerpt and change the text
		function change_excerpt_more()
		{
		  function new_excerpt_more($more)
			{
			// Use .read-more to style the link
			  return '<span class="continue-reading"> <a href="' . get_permalink() . '">Continue Reading &raquo;</a></span>';
			}
		  add_filter('excerpt_more', 'new_excerpt_more');
		}
		add_action('after_setup_theme', 'change_excerpt_more');

*   Save `functions.php` file and reload home / blog page.

###  Remarks

<note> *If there is no `content.php` file in your child theme folder, just copy `content.php` file from parent theme and paste it in to child theme folder. Then edit this `content.php` file in child theme folder. Please read this post about WordPress child theme before.

**Same like `content.php` file, a `functions.php` file is required in our child theme folder. It is not a copy of parent theme's `function.php` file. </note>
