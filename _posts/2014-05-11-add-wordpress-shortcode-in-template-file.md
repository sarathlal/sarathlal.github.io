---
title: Add WordPress shortcode in template file
author: sarathlal
layout: post
tags:
  - WordPress
---
The shortcodes are special tag in WordPress that we can enter into content area like post or page that gets replaced with different content when viewing the post on the website.

When we deal with WordPress plugins, almost of them generate shortcode for us. Also we can generate our own shortcode for our custom functions & hacks. We can directly use these shortcodes in pages and posts.

But in some situations, we want to use these shortcodes in template files. In such cases, we can use a simple WordPress function, `do_shortcode` in our theme files.

	<?php echo do_shortcode('[your_shortcode]'); ?>

Try this simple WordPress function & make our theme as fully loaded.
