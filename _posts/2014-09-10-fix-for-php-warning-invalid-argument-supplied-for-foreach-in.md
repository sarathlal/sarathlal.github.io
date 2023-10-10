---
title: 'Fix for PHP Warning &#8211; Invalid argument supplied for foreach() in …'
author: sarathlal
layout: post
tags:
  - PHP
---
While working on a WordPress project, I got a PHP warning.

	Warning: Invalid argument supplied for foreach() in …

We can easily hide warnings in PHP. But I like to learn more about such simple matters in deep.

Actually this error is coming from a foreach loop. I just try to `var_dump` values in an array using this foreach loop.

	foreach ($items as $item) {
	 // ...
	}

In the PHP manual, it says that

> The foreach construct provides an easy way to iterate over arrays. foreach works only on arrays and objects, and will issue an error when you try to use it on a variable with a different data type or an uninitialized variable.

This is the basic cause behind this warning. We are passing something to foreach loop that is not an array.

To solve this warning, we have two simple options at here.

##  Solution 1

We can check the type of that variable & if it is an array, then only pass it to the foreach loop.

	if (is_array($items)) {
	 foreach ($items as $item) {
	 // ...
	 }
	}

Now we ensure that we have an array for foreach loop.

##  Solution 2

We can also solve this warning by cast that variable to an array in the loop. This is a lot cleaner, requires less typing and only needs one edit on a single line.

	foreach ((array) $items as $item) {
	 // ...
	 }

If we cast any value to an array, we will get an array whatever value it was.
