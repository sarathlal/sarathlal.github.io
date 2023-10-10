---
title:  Make a string's first character as uppercase - PHP
layout: post
tags:
  - PHP
---

To make a string's first character as uppercase, we can use a PHP function called `ucfirst`.

	string ucfirst ( string $string )

Returns a string with the first character of `$string` capitalized, if that character is alphabetic.

####  Example

	$foo = 'hello world!';
	$foo = ucfirst($foo);             // Hello world!

	$bar = 'HELLO WORLD!';
	$bar = ucfirst($bar);             // HELLO WORLD!
	$bar = ucfirst(strtolower($bar)); // Hello world!
