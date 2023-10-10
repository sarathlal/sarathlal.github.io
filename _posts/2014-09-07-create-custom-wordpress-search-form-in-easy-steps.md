---
title: Create custom WordPress search form in easy steps
author: sarathlal
layout: post
tags:
  - WordPress
---
When customizing themes for WordPress, often we want to style & use search forms in our template.

We can easily call WordPress search form in our template files.

	<?php get_search_form(); ?>

This call will render WordPress default search form in our pages.

If we don&#8217;t have a `searchform.php` file in our theme, WordPress automatically generate a search form.

But we have limited customization option at there. So we are going to make that file manually and then style it according to our design.

First make a new PHP file inside our **theme / child theme** and name it as **searchform**. It is a clone of default WordPress search form. Then add below code in to that one.

	<form role="search" method="get" id="searchform" action="<?php echo home_url( '/' ); ?>">
	 <div><label class="screen-reader-text" for="s">Search for:</label>
	 <input type="text" value="" name="s" id="s" />
	 <input type="submit" id="searchsubmit" value="Search" />
	 </div>
	</form>

Add CSS selectors ( class & id ) on this form elements & then style them. That&#8217;s enough.
