---
title: Create dynamic image using Python with Pillow package
layout: post
tags:
  - Python
  - Automation
  - DevOps
---

The `Pillow` is an amazing `Python` Imaging Library. Often I need to make dynamic images & here is the basic code to create an image using `Python` with `Pillow` package.

	from PIL import Image
	import random

	width = 400
	height = 400

	img  = Image.new( mode = "RGB", size = (width, height), color = tuple(random.choices(range(256), k=3)) )
	img.save("your_image_name.jpg")


To do an automated testing, I need one thousand images in a directory. To generate those images, I have used the above code with a loop. Within 20 seconds, the images are ready in my directory!

	from PIL import Image
	import random

	width = 400
	height = 400
	
	for i in range(1,1000):
		img  = Image.new( mode = "RGB", size = (width, height), color = tuple(random.choices(range(256), k=3)) )
		img.save("img_"+str(i)+".jpg")

### Related links

1. [Pillow home](https://python-pillow.org/){:target="_blank"}
2. [Pillow Documentation](https://pillow.readthedocs.io/){:target="_blank"}
