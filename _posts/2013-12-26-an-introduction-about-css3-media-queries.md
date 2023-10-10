---
title: An introduction about CSS3 media queries
author: sarathlal
layout: post
tags:
  - CSS
  - CSS3
---

The media queries are expressions to check certain media conditions like resolution of the device, viewing area resolution and device orientation. Then we can apply different styles for our web pages for different media with this media queries.

In CSS2, it allows us to specify styles for specific media type such as screen or print. Same like, now in CSS3 it allow us to specify styles for user media like laptop, tablet & phone etc.

for example, consider that we have one style sheet for large displays and a different style sheet specifically for mobile devices. The media queries in CSS3 help us to tailor our web pages to different resolutions and devices without changing the content.

### Max Width

	@media screen and (max-width: 600px) {
	  .class {
		background: #000;
	  }
	}

The above media query and expression make the specific class element’s background as Black, if the viewing area is less than 600px.

If we want to link to a separate stylesheet ( 600.css ), we want to insert the following line of code in between the head section of our web page.

	<link rel="stylesheet" media="screen and (max-width: 600px)" href="600.css" />

### Min Width

	@media screen and (min-width: 900px) {
	  .class {
		background: Red;
	  }
	}

The above media query and expression make the specific class element back ground as Red, if the viewing area is more than 900px. Multiple Media Queries

We can combine multiple media queries. The following code will apply if the viewing area is between 600px and 900px.

	@media screen and (min-width: 600px) and (max-width: 900px) {
	  .class {
		background: #333;
	  }
	}

### Device Width

Same like above examples with viewing area, we can apply styles based on device width using media queries.

	@media screen and (max-device-width: 480px) {
	  .class {
		background: #000;
	  }
	}

The above media query and expression make that specific class background as black, if the device width is less than 480px.

**max-device-width means the real resolution of the device and max-width means the viewing area resolution.**

### Example stylesheet


	/*Add default CSS expressions at here*/

	/* Laptop/Tablet (1024px) */
	@media only screen and (min-width: 481px) and (max-width: 1024px) and (orientation: landscape) {

		   /*CSS expressions for Laptop and tablet with a screen 1024px goes here*/
	}

	/* Tablet Portrait (768px) */
	@media only screen and (min-width: 321px) and (max-width: 1024px) and (orientation: portrait) {

		/*CSS expressions for tablet in portrait mode goes here*/

	}

	/* Phone Landscape (480px) */
	@media only screen and (min-width: 321px) and (max-width: 480px) and (orientation: landscape) {

		/*CSS expressions for Phone in landscape mode goes here*/

	}

	/* Phone Portrait (320px) */
	@media only screen and (max-width: 320px) {

		/*CSS expressions for Phone in portrait mode goes here*/

	}
