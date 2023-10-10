---
title: Check if list elements are integer - Python
layout: post
tags:
  - Python
---

In a python script, I have a list item and I want to confirm that all elements in that list are integer.

Below, you can find the line of code I have used to confirm the elements are integer in a list.

	my_list = [1, 2, 3]
	p = all(isinstance(item, int) for item in my_list)
	print p
	>>>True
	my_list = [1, 2, 3.5]
	p = all(isinstance(item, int) for item in my_list)
	print p
	>>>False

