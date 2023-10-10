---
title: Check a number is even or odd in PHP
author: sarathlal
layout: post
tags:
  - PHP
---
Today, I want to check weather a number is even or odd in my PHP appliation.

We can simply use an if else statement for this pourpose.

	<?php
	if($num % 2)
	{
	 echo 'Odd number';
	} else{
	 echo 'Even number';
	}
	?>

If you like shortcodes in your program, we can write it in a single line.

	<?php print ($i % 2 == 0 ? Even number : Odd number); ?>
