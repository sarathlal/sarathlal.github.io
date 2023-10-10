---
title: Style placeholder text of input fields - CSS3
author: sarathlal
layout: post
tags:
  - CSS
  - CSS3
  
---

In default, the placeholder texts have a light gray color fonts and an ugly look according to browser default styles. But we can uniformly style these placeholder text in all modern browsers using CSS3.

To style placeholder texts, we want to use vendor prefix CSS properties.

	/* all */
	::-webkit-input-placeholder {
	   color: red;
	}

	:-moz-placeholder { /* Firefox 18- */
	   color: red;  
	}

	::-moz-placeholder {  /* Firefox 19+ */
	   color: red;  
	}

	:-ms-input-placeholder {  
	   color: red;  
	}

If you like to apply different style on each input field placeholder, just target specific input field and then apply styles on it.

	/* individual: webkit */
	#field1::-webkit-input-placeholder { color:#00f; }
	#field3::-webkit-input-placeholder { color:#090; background:lightgreen; text-transform:uppercase; }

	#field1::-moz-placeholder { color:#00f; }
	#field2::-moz-placeholder { color:#090; background:lightgreen; text-transform:uppercase; }
