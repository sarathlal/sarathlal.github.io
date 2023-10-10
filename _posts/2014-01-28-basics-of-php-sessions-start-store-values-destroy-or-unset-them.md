---
title: 'Basics of PHP sessions &#8211; start, store values &#038; destroy or unset them'
author: sarathlal
layout: post
tags:
  - PHP
---
The session is the time span begin from when a person start to interact with something & end until he quit that one.

In PHP web applications, when a user visit a web page in server, a session can be started & when he quit the browser, that session will be ended.

In PHP, The sessions are not automatically started. We want to start PHP session using a PHP function & then we can store some information for that particular session only.

We use `$_SESSION` array to store session data & its values are available on all web pages in that application until we quit the browser.

The important things are the session variable are stored in server & when our application start a session for a user, it is unique for him. This unique session end until he quit the browser.

##  Start a session

Starting a session is too simple. We just want to call `session_start()` function in PHP. But we must done this at the beginning of our PHP code, and must be done before any text, HTML, or JavaScript is sent to the browser.

	<?php
	// start the session!
	session_start();
	##  Store some data for that session

I already say that, we use `$_SESSION` array to store session data. After starting our session, we can store our data in to `$_SESSION` array.

	// store session data
	$_SESSION["username"] = "Your_name";

##  Retrieve that stored data

We already start a PHP session & then store some data in session variable to use in another pages.

Now we are going to use that session data in a different web pages. This is also too simple. We just want to start the session again in that page.

When we start the session again in a different page in our application, the data stored in `$_SESSION` array is also available on this page.

	<?php
	// Start the session means continue the session
	session_start();
	// retrieve session data
	echo "Username = " . $_SESSION["username"];

But if we are going directly to the second page with out visiting first page, the second page can&#8217;t get the Username because we stored Username in `$_SESSION` array from the first page.

##  End this session

We have different options at here.

To delete a single session value, we want to use the unset() function.

	<?php
	session_start();
	// delete the username value
	unset($_SESSION["username"]);

To unset all of the session&rsquo;s values, we can use the `session_unset()` function.

	<?php
	session_start();
	// delete all session values
	session_unset();

These both examples unset stored data in session variable. But still we can use same session variable to store other values.

If we like to completely stop using this session, like logout, we want to use the `session_destroy()` function.

	<?php
	session_start();
	// Kill the session
	session_destroy();

By this `session_destroy()` function, we completely destroy our session. This method is highly recommended if we don&#8217;t need to use the session any more.

The session in PHP is very simple but very powerful functionality in PHP that provide efficient solution to transfer sensitive data between web pages. So play well with sessions & use them for our PHP applications.
