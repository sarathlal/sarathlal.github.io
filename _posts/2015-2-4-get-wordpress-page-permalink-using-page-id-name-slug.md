---
title: Get WordPress Page permalinks in template files using Page ID, Name or Slug
author: sarathlal
layout: post
tags:
  - WordPress
---

In some WordPress theme customizations, I want to get page permalinks for different pages in template files. We can use WordPress default functions, `get_page_link()` &  `get_permalink()` in such situations.

### WordPress page URL using Page ID

	<a href="<?php echo get_page_link(Page ID); ?>">Page Title</a>

*Example:*

	<a href="<?php echo get_page_link(40); ?>">Events</a>

### WordPress page URL using Page Title

	<a href="<?php echo get_permalink( get_page_by_title( 'Page Title' ) ); ?>">Page Title</a>

*Example:*

	<a href="<?php echo get_permalink( get_page_by_title( 'Events' ) ); ?>">Events</a>

### WordPress page URL using Page slug

	<a href="<?php echo get_permalink( get_page_by_path( 'Page slug' ) ); ?>">Page Title</a>

*Example:*

	<a href="<?php echo get_permalink( get_page_by_path( 'events' ) ); ?>">Events</a>

### WordPress page URL of Hierarchical Pages using Page slug.

If we have a page in hierarchy, we want to pass the full slug including the parent to the get_page_by_path function.

	<a href="<?php echo get_permalink( get_page_by_path( 'Parent Page slug/child Page slug' ) ); ?>">Page Title</a>

*Example:*

Now we have a child page called “Parties” with a parent page called “Events”.

	<a href="<?php echo get_permalink( get_page_by_path( 'events/parties' ) ); ?>">Parties</a>
