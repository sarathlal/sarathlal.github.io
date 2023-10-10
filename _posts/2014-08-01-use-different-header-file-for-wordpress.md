---
title: Use different header file for WordPress
author: sarathlal
layout: post
tags:
  - WordPress
---
To display header in WordPress, normally we use `get_header()` function & it render header from `header.php `file in our theme.

But if we want to use different header files for different template pages in WordPress, just pass the name of the header file with `get_header()` function call.

     <?php get_header( $name ); ?>

For example, to call `header-blog.php` file, we want to call `<?php get_header( 'blog' ); ?>.`

A good example to retrieve multiple header on multiple WordPress page is given below.

	<?php
	if ( is_home() ) :
	 get_header( 'home' );
	elseif ( is_404() ) :
	 get_header( '404' );
	else :
	 get_header();
	endif;
	?>
