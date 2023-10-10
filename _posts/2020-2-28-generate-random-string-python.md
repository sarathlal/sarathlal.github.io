---
title: Generate random string - Python
layout: post
tags:
  - Python
---

Getting a random string is almost required in application development. To get a random string using Python, we can use the below function.

	import secrets 
	import string

	def generate_random_string(length = 6):
		alphabet = string.ascii_uppercase + string.digits
		random_string = ''.join(secrets.choice(alphabet) for i in range(length))
		return random_string

	my_string = generate_random_string(8)
	print(my_string)

Output

	QEFBG0G1
