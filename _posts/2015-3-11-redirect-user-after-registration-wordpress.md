---
title: Redirect user after successfull registration - WordPress
author: 
layout: post
tags:
  - WordPress
---

When we allow user registration on our WordPress site, WordPress generate a message to check their email after each successful registration.

But if you are interested to redirect your user in to a specific page after their successfull registration, just use below code snippet in your theme’s or child theme’s functions.php file.
	function qdtyo_registration_redirect(){
		return home_url( '/finished/' );
	}
	add_filter( 'registration_redirect', 'qdtyo_registration_redirect' );

