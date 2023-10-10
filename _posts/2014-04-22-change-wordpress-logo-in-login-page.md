---
title: Change WordPress logo in Login page
author: sarathlal
layout: post
tags:
  - WordPress
---
In default WordPress installation, when we go to login page, we can find a WordPress logo in our login form.

When we build Blog / CMS for clients, customizing WordPress in all aspect is a good approach. In the case of login screen, either we can make custom login page or we can change WordPress logo with our custom logo.

So for simple applications, now we are going to change WordPress logo with our custom logo with the help of a simple code snippet.

Add below function in our child theme&#8217;s `functions.php` file.

	function my_login_logo() { ?>
		<style type="text/css">
		body.login div#login h1 a {
			background-image: url(<?php echo get_stylesheet_directory_uri(); ?>/images/your-logo.png);
			padding-bottom: 30px;
		}
		</style>
	<?php }
	add_action( 'login_enqueue_scripts', 'my_login_logo' );


This function will override WordPress default login screen. Always remember to add our logo in our child theme&#8217;s `images` folder.
