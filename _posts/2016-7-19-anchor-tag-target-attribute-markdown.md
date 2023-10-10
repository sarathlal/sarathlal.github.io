---
title:  Anchor tag with target attribute - Markdown
layout: post
tags:
  - Jekyll
  - Markdown
  
---

In Markdown, there is simple way to write anchor tag.

	[Your Text](http://yourdomain.com)
	
The above line will generate `<a href="http://yourdomain.com">Your Text</a>` anchor tag.

There is a target attribute for anchor tag and it can control the behaviour of our link.

	<a href="http://yourdomain.com" target="_blank">Your Text</a>
	
When we click on this link, it will open the URL in a new browser tab.

In Markdown also, we can add this target attribute.

	This is [My Home Page](http://sarathlal.com){:target="_blank"}
