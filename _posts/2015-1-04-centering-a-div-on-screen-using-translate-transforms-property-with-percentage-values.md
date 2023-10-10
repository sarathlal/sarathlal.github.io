---
title: Centering a DIV on screen using translate() transforms property with percentage values
author: sarathlal
layout: post
tags:
  - CSS3
  - CSS
---

There is a simple method to center an element on screen in CSS3. We are going to use `translate()` transforms property in CSS3 for this quick hack.

	.center {
		 position: absolute;
		 left: 50%;
		 top: 50%;
		 transform: translate(-50%, -50%);
		 width: 48%;
		 height: 59%;
	}
