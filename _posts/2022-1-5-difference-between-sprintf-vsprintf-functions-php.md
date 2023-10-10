---
title: Difference between sprintf() & vsprintf() functions in PHP
layout: post
tags:
   - PHP
---

### sprintf()

The sprintf() function writes a formatted string to a variable.

	<?php
	$number = 9;
	$str = "Beijing";
	$txt = sprintf("There are %u million bicycles in %s.",$number,$str);
	echo $txt;
	?>

The arg1, arg2, ++ parameters will be inserted at percent (%) signs in the main string. This function works "step-by-step". At the first % sign, arg1 is inserted, at the second % sign, arg2 is inserted, etc.

Note: If there are more % signs than arguments, you must use placeholders. A placeholder is inserted after the % sign, and consists of the argument- number and "\$".

### vsprintf()

Unlike sprintf(), the arguments in vsprintf(), are placed in an array. The array elements will be inserted at the percent (%) signs in the main string.

	<?php
	$number = 9;
	$str = "Beijing";
	$txt = vsprintf("There are %u million bicycles in %s.",array($number,$str));
	echo $txt;
	?>
