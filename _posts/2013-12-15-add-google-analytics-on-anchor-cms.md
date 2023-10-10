---
title: Add Google analytics on Anchor CMS
author: sarathlal
layout: post
tags:
  - Anchor CMS
---
Have you ever tried to add Google analytics script on Anchor CMS. I have a simple & efficient way to do it with site variable in Anchor CMS.

The anchor CMS is a light weight, fast & minimal open Source blog engine written in PHP. It have some amazing options and now we use one of it, site variable to add Google analytics code on Anchor CMS.

The site variable is a option to add variables for site wise in Anchor CMS. We can access its value as a site meta in any where in our template files. We use this option to add our analytics script in our theme&#8217;s header or footer.

Before further reading, I consider that you have your Google Analytics code with you. If else, you want to make a analytics script for your site from Google analytics official website.

**Step 1:** Add a new site variable in admin area of Anchor CMS.

*   First go to admin interface of Anchor CMS, then select extend menu & after choose its site variable option.
*   Add a new variable with a unique name & your analytics script as its value. We want to add `<script type="text/javascript">` tag in beginning & `</script>` tag at the end of our analytics script.

For example, value for `g_analytics`, my site variable is look like below one.

	<script type="text/javascript">
	(function(b,o,i,l,e,r){b.GoogleAnalyticsObject=l;b[l]||(b[l]=
	function(){(b[l].q=b[l].q||[]).push(arguments)});b[l].l=+new Date;
	e=o.createElement(i);r=o.getElementsByTagName(i)[0];
	e.src='//www.google-analytics.com/analytics.js';
	r.parentNode.insertBefore(e,r)}(window,document,'script','ga'));
	ga('create','UA-xxxxxx-1');ga('send','pageview');
	</script>

The `g_analytics` is the name for my site variable & you can use any unique name for it.

*   Save the variable and then after we can use our variable for further tweaks.
*   After save a site variable, we can see all created site variable in site variable screen.
*   Select our Google analytics site variable from that screen & it give a edit screen for that variable.
*   Below our name & value of that variable, we can see a php snippet like below example. We can use this site variable in our theme files.
 
		<?php echo site_meta('g_analatycs'); ?>

**Step 2**: Now we want to use this snippet in our theme files.

*   Now we can open our theme&#8217;s footer or header file.
*   Just insert the php snippet for site variable in to footer or header file. Always remember to add this snippet inside body tag of header or footer file.
*   Save file & we completed all steps.

In feature, if you want to edit your Google analytics code or customize it, just go to site variable option in admin end & edit your script in value field. This is the biggest advantage of this method because our analytics script is automatically updated without any editing in theme files.
