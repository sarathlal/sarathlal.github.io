---
title: The basics about WordPress template hierarchy
author: sarathlal
layout: post
tags:
  - WordPress
---
The template files have a big role in WordPress. We use different template files to render the whole WordPress site.

The WordPress have a predefined template hierarchy. That means, to render a specific type page, WordPress always look some template file & if it is absent, then it use another template file.

If we want to deal with themes in WordPress, having a basic idea about these template hierarchy will be useful. Actually, the themes are a collection of template files with some extra files like images etc.

The important template files used in WordPress themes are `header.php`, `footer.php`, `index.php`, `single.php`, `page.php`, `archive.php` & `404.php` etc.

Some of these files are used to render the part of web page like `header.php` & `footer.php` etc. Some others have predefined function in WordPress site.

Now we can check the priority of these files to render different type pages in WordPress.

I just copied all these information from [WordPress Codex][1]. All credits are going to WordPress & its amazing documentation team. My role is only filter that Codex page & republish the essential content.

###  404 (Not Found) display

Template file used to render a Server 404 error page

1.  404.php
2.  index.php

###  Search Result display

Template file used to render a Search Results Index page

1.  search.php
2.  index.php

###  Custom Taxonomies display

Template file used to render the Archive Index page for a Custom Taxonomy

1.  taxonomy-{taxonomy}-{term}.php &#8211; If the taxonomy were sometax, and taxonomy&#8217;s term were someterm WordPress would look for taxonomy-sometax-someterm.php.
2.  taxonomy-{taxonomy}.php &#8211; If the taxonomy were sometax, WordPress would look for taxonomy-sometax.php
3.  taxonomy.php
4.  archive.php
5.  index.php

###  Home Page display

Template file used to render the Blog Posts Index, whether on the site front page or on a static page.

1.  home.php
2.  index.php

###  Attachment display

Template file used to render a single attachment (attachment post-type) page

1.  MIME_type.php &#8211; it can be any MIME type (image.php, video.php, application.php). For text/plain, in order:</p> 
    1.  text.php
    2.  plain.php
    3.  textplain.php
2.  attachment.php
3.  single-attachment.php
4.  single.php
5.  index.php

###  Single Post display

Template file used to render a single post page.

1.  single-{post_type}.php &#8211; If the post type were product, WordPress would look for single-product.php.
2.  single.php
3.  index.php

###  Page display

Template file used to render a static page (page post-type)

1.  custom template file &#8211; The Page Template assigned to the Page. See get*page*templates().
2.  page-{slug}.php &#8211; If the page slug is recent-news, WordPress will look to use page-recent-news.php
3.  page-{id}.php &#8211; If the page ID is 6, WordPress will look to use page-6.php
4.  page.php
5.  index.php

###  Category display

Template file used to render a Category Archive Index page

1.  category-{slug}.php &#8211; If the category&#8217;s slug were news, WordPress would look for category-news.php
2.  category-{id}.php &#8211; If the category&#8217;s ID were 6, WordPress would look for category-6.php
3.  category.php
4.  archive.php
5.  index.php

###  Tag display

Template file used to render a Tag Archive Index page

1.  tag-{slug}.php &#8211; If the tag&#8217;s slug were sometag, WordPress would look for tag-sometag.php
2.  tag-{id}.php &#8211; If the tag&#8217;s ID were 6, WordPress would look for tag-6.php
3.  tag.php
4.  archive.php
5.  index.php

###  Author display

Template file used to render an Author Archive Index page

1.  author-{nicename}.php &#8211; If the author&#8217;s nice name were rami, WordPress would look for author-rami.php.
2.  author-{id}.php &#8211; If the author&#8217;s ID were 6, WordPress would look for author-6.php.
3.  author.php
4.  archive.php
5.  index.php

###  Date display

Template file used to render a Date-Based Archive Index page

1.  date.php
2.  archive.php
3.  index.php

###  Archive display

Template file used to render the Archive Index page for a Post Type

1.  archive-{post_type}.php &#8211; If the post type were product, WordPress would look for archive-product.php.
2.  archive.php
3.  index.php

These are the file hierarchies to render different type pages in a WordPress site. As stated above, all of this informations are copied from [WordPress Codex][1]. You can read the original document at there.

Any way, I believe that this quick reference will help us in our feature WordPress development. Thanks to WP & its Codex.

 [1]: https://codex.wordpress.org/Template_Hierarchy
