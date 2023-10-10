---
title: Make custom styles only for Mozilla Firefox
author: sarathlal
layout: post
tags:
  - Browser Hacks
---
Some HTML elements & styles are look like broken in some Firefox versions. If you like to optimize your design for Mozilla Firefox, we can use a simple filter for Firefox only.

	@-moz-document url-prefix() { 
	 .inner-container {
	 padding: 4px 4px 2px 0;
	 }
	}

Any CSS rule that starts with `@-moz-` is a Gecko-engine-specific rule, not a standard rule. That is, it is a Mozilla-specific extension.

Another option is to use the domain() filter. For example `@-moz-document domain(http://google.com) {...}` will apply the enclosed CSS rules only on the `http://google.com` domain in Firefox.

The url-prefix rule applies the contained style rules to any page whose URL starts with it in Gecko (Mozilla Firefox). When used with no URL argument like `@-moz-document url-prefix(),` it applies to ALL pages.
