---
title: 'Insert content after each posts with filter hook - WordPress'
author: sarathlal
layout: post
tags:
  - WordPress
---
If we want to add some content in single posts, Everyone like to edit `single.php` file in our theme directory. In almost WordPress themes, this `single.php` file is used to render single posts.

We just want to add our content after the `the_content()` function.

Today we are going to use another method to achieve this same functionality. Just copy & paste below code in to our theme&#8217;s `functions.php` file.

	function insertFootNote($content) {
		if(!is_feed() && !is_home()) {
				$content.= "<div class='subscribe'>";
				$content.= "<h4>Enjoyed this article?</h4>";
				$content.= "<p>Subscribe to our  <a href='http://feed.example.com'>RSS feed</a> and never miss updates!</p>";
				$content.= "</div>";
		}
		return $content;
	}
	add_filter ('the_content', 'insertFootNote');

In this code snippet, we just make a new function named as `insertFootNote()` with our additional content. Then use WordPress filter hook to add this additional content with content from Database.

I always suggest you to try hacks & code snippet as much as possible in different ways. It will improve our knowledge & help to master in our domain.
