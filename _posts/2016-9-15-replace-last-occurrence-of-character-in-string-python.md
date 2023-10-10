---
title: Find and replace last occurrence of a character in string - Python
layout: post
tags:
  - Python
---

	old_string = "MK-36-W-357-IJO-36-MDR"
	k = old_string.rfind("-")
	new_string = old_string[:k] + "." + old_string[k+1:]
	print(new_string)
	
	#Result will be MK-36-W-357-IJO-36.MDR
