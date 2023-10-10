---
title:  Display an array in a readable format - PHP
layout: post
tags:
  - PHP
---

When debugging PHP projects, often I want to know the content in large multi dimensional arrays. We can simply `var_dump` the object or array, but there is little hardness on reading content.

Here is a simple trick to display content in multi dimensional array in a neat & human readable format.

	//$data is our variable
	print "<pre>";
	print_r($data);
	print "</pre>";

