---
title: Vertical margin and padding are not working in labels – Quick fix
author: sarathlal
layout: post
tags:
  - CSS
---

When creating forms in web pages, we want to use labels with input fields. To style these label elements, I always tries to add padding and margin on top and bottom with other styles.

But in default, this margin property and padding property on bottom and top on these label elements have no roles in web pages!.

Basically label elements are inline elements and vertical margins and vertical padding will not have any effect on such inline elements.

If still we want to apply margin and padding on top and bottom, there is a quick fix.

First make these labels as inline-block elements and then apply these vertical padding and vertical margin property on it. That is enough.

	label {
	 display:inline-block;
	 margin-top:5px;
	}
