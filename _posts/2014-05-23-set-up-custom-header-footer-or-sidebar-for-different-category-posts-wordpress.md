---
title: 'Set up custom header, footer or sidebar for different category posts &#8211; WordPress'
author: sarathlal
layout: post
tags:
  - WordPress
---
Have you bored with same layout for all posts in your WordPress blog / CMS?

We choose WordPress as our platform because & its community offer thousands of awesome hacks & tips to make it as unique by customization.

So today, we are going to apply a simple hack to set up custom header, footer or sidebar for our blog posts. Instead of setting up custom layout for each & every posts, we choose category to set up custom header, footer or sidebar.

Before further reading, we need basic knowledge to create custom template file in WordPress. If so, first we want to open `index.php` file in our child theme folder.

When we open `index.php` file, we can find function calls like `get_header()`,`get_footer()` and `get_sidebar()` etc.

When we call `get_header()` function, it includes the `header.php` template file from our current theme&#8217;s directory. If a name is specified then a specialized header `header-{name}.php` will be included.

Now we are going to use this point to includes custom header in our `index.php` file.

In our `index.php` file, just replace `get_header()` header code with the below code snippet.

	<?php if (is_category('Blogging')) {
		get_header('blogging');
	} else {
		get_header();
	} ?>

I think you can easily catch the logic behind this snippet. It says that, if current category is `Blogging`, include a custom header template file with the name `header-blogging.php` instead of normal header template file `header.php`.

Else utilize our theme&#8217;s default header template file `header.php`.

We can use this same logic in footer & sidebar.

For custom footer, replace `get_footer()` line with below snippet. We need `footer-blogging.php` template file in our theme directory.

    <?php if (is_category('Blogging')) {
		get_footer('blogging');
    } else {
		get_footer();
    } ?>

For custom sidebar, replace `get_sidebar()` line with below snippet. We need `sidebar-blogging.php` template file in our theme directory.

    <?php if (is_category('Blogging')) {
		get_sidebar('blogging');
    } else {
		get_sidebar();
    } ?>

Try this hack and make your site layout more impressive. If we have a little bit of creativity & basic knowledge to code, the WordPress is always amazing.
