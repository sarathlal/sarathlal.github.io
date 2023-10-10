---
title: Redirect user after password reset - WordPress 
layout: post
tags:
  - WordPress
---

In WordPress, after user submit the form to reset the password, new password will saved on database & a message will show on the page about the status.

In one of my recent project, I have to redirect my user to home page after password reset. If you like to do so, use below code snippet.

	function wpse_lost_password_redirect() {
	   wp_redirect( home_url() );
	   exit;
	}
	add_action('password_reset', 'wpse_lost_password_redirect');
