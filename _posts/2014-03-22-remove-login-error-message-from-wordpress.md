---
title: Remove login error message from WordPress
author: sarathlal
layout: post
tags:
  - WordPress
---
When we fail to login to the WordPress, it shows different error message telling that what went wrong from our side. This is good in normal cases because it help to realize the problem.

But it might also be good for people who want to hack our blog because they can easily guess some common username & password for our blog & ensure that they exist by this way.

There is a simple hack to prevent WordPress from displaying error messages on failed logins.

We just want to add a single line of code in our child theme&#8217;s `functions.php` file.

	add_filter('login_errors',create_function('$a', "return null;"));

Save the file, logout and try to login with an invalid username or password. There is no more messages are displayed if you fail to login.

Here we added a simple hook to overwrite the default `login_errors()` function of WordPress. The custom function that we created returns only null & so the message displayed will be a blank string.
