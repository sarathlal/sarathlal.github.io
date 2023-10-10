---
title: 'Change default Gravatar for comments &#8211; WordPress'
author: sarathlal
layout: post
tags:
  - WordPress
---
In default, WordPress use `mystery man` as Gravatar for comments. But if you like to brand your users default garvatar, we can easily achieve this with a simple function & filter.

First we want to open our `functions.php` file in child theme directory. Then add below filter & function on it.

	if ( !function_exists('s_addgravatar') ) {
		function s_addgravatar( $avatar_defaults ) {
			$myavatar = get_bloginfo('template_directory') . '/images/your_avatar.jpg';
			$avatar_defaults[$myavatar] = 'Custom Avatar';
			return $avatar_defaults;
		}
		add_filter( 'avatar_defaults', 's_addgravatar' );
	}

Then add our branded new avatar image in to child theme&#8217;s `images` folder & edit the 3rd line of code according to our image name.

We almost completed the coding. Next we want to set up this new avatar as default avatar for discussion in WordPress back-end.

Just go to Settings >> Discussion settings & now we can see our new avatar name `Custom Avatar` in Default avatar settings. So choose `Custom Avatar` as Default avatar & save changes.
