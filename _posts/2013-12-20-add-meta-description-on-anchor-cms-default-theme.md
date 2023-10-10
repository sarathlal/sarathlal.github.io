---
title: Add meta description on Anchor CMS default theme
author: sarathlal
layout: post
tags:
  - Anchor CMS
---
In Anchor CMS default themes (version 0.9.2), it show the site description as a meta description for all pages & posts. Basically, the developers of Anchor CMS don&#8217;t like to consider such SEO matters.

If Google realize that our meta description is not good for our content, it will show some random lines of text related with our content in our web pages as a search description!

But if you are a SEO buddy, you have option to deliver unique meta description for Anchor CMS. With this code snippet, we use post description as a content for meta description tag. That means, our post / page description will appear as search description in Search Engine result Pages.

Currently, Anchor CMS don&#8217;t support plugins & child themes (version 0.9.2). So now we try to edit our theme files.

*   First we want to select our current theme from theme folder.
*   Then we want to open header file (`header.php`) inside theme folder.
*   Just replace our current title tag with our modified title & meta description tag shown below.
</ul>

	<?php if(is_article()): ?>
		<title><?php echo article_title(); ?> | <?php echo site_name(); ?></title>
		<meta name="description" content="<?php echo article_description(); ?>">
	<?php elseif(is_homepage()): ?>
		<title><?php echo site_name(); ?> | <?php echo site_description(); ?></title>
		<meta name="description" content="<?php echo site_description(); ?>">
	<?php elseif(is_page()): ?>
		<title><?php echo page_title(); ?> | <?php echo site_name(); ?></title>
		<meta name="description" content="<?php echo site_description(); ?>">  
	<?php endif; ?>


*   Save file & reload your blog. You can view source code of web page to ensure that our meta description tag show that post&#8217;s description as a content.
