---
title: 'Exclude categories from category list - WordPress'
author: sarathlal
layout: post
tags:
  - WordPress
---
Most blogs include a list of categories in sidebar for visitors to easily find there interested content.

In default, WordPress offer category widget to make it easier. But we have limited control on this default category widget.

In certain situations, we want to hide some categories from our category list. In such conditions, we can use a single line of code instead of category widget.

	<?php wp_list_cats(); ?>

This line of code list all categories in our WordPress blog. To exclude some categories, we add a parameter with this function.

	<?php wp_list_cats('exclude=4, 5'); ?>

The above line of code will display a category list without categories they have ID of four & five. We can get the category ID from the WP dashboard.
