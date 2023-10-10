---
title: Hide text using CSS – a neat and better approch
author: sarathlal
layout: post
tags:
  - CSS3
  - CSS
---

If we want to hide some text content in our HTML page, we can simply use CSS `display` property to hide them.

	.hide-text {
	 display: none;
	}

But this will completely avoid rendering of text and by the way it will hide our content for devices like screen readers etc.

So to avoid this situations, we can use a better method to hide text.

	.hide-text {
	 text-indent: 100%;
	 white-space: nowrap;
	 overflow: hidden;
	}
