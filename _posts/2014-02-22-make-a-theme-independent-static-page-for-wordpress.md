---
title: Make a theme independent static page for WordPress
author: sarathlal
layout: post
tags:
  - WordPress
---
When making customization in WordPress themes for clients, often I want to deal with custom designed static pages. It may be a landing page or even a home page for some of them.

Some of these static page is 100% independent with there themes. I want to add some static HTML content and styles on that pages.

In such situations, we can use benefits of WordPress template hierarchy to achieve our goal.

I thought you already made a new page from WordPress dashboard. Just note its page slug or ID for further use.

First we want to make a child theme for our theme & then copy `page.php` from parent theme to our child theme. This `page.php` is used to render single pages in WordPress themes.

Then rename that file with our page slug (page URL) like `page-about-me.php`. Else rename that file with our page ID like `page-6.php`.

By doing this step, we override our current theme&#8217;s template hierarchy with our new page template file.

Normally WordPress themes use `page.php` file to render single pages. But now we added a new page template `page-{slug}.php` or `page-{id}.php` & both of these have more weight than `page.php` in template hierarchy.

Then remove all content from that file and put our HTML at there. That is enough.
