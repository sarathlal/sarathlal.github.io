---
title: 'ID or Class - Selectors and there semantic use in HTML'
author: sarathlal
layout: post
tags:
  - HTML
---
To make web pages, we can use two selectors, Class and ID to style our HTML elements using CSS. They have there own semantic use & we want to aware about them.

##  The ID

The ID selector is use to specify style for a single, unique element. It uses the id attribute of the HTML element, and is defined with a hash, `#`.

###  Example code

	<p id="centered">Lorem</p>

	#centered { text-align: center; }


##  The Class

The Class selector is use to specify style for a group of elements. This allows us to set a particular style for many HTML elements with the same class. The class selector uses the HTML class attribute, and is defined with a dot, `.`.

###  Example code

	<p class="centered">Lorem</p>

	.centered { text-align: center; }

##  Why they are different?

The simple answer is that the IDs are unique, and Classes are NOT unique.

When considering ID,

*   Each HTML element can have only one ID.
*   Each page can have only one HTML element with that ID.

But in Classes,

*   We can use the same class on multiple HTML elements.
*   We can use multiple classes on the same HTML element.

Considering the first example code, we have an ID `centered` and it will centering that paragraph. If we want to center another h2 element, we can&#8217;t use that ID `centered` again. If we use that ID again for some elements, the code never been validated.

In second example, we have a class `centered` and it will centering that paragraph. We can use this same class in every HTML elements that we want to center and it is a validated code.

##  Why I want to use Classes than ID?

Every one advice to use Class selectors than ID. So getting the causes behind this advice is always interesting.

*   The ID selector is use to style unique HTML element. So we can&#8217;t reuse that for another elements.
*   The ID is more specific. This ultra specificity will make some unimaginable effects in feature or further development.

This two important reasons are pull back us from using ID selector in HTML elements.

##  So I want to avoid the use of ID selectors?

No and never. It is depend with context of our project.

First understand that ID selector are curated for unique element. Then realize our unique elements and use ID selectors for them if necessary. Same time get aware about where they can cause for our headaches.

In some circumference, we must want to use ID selectors.

We are familiar with &lsquo;Skip to navigation&rsquo; or &lsquo;Jump to content&rsquo; links in pages, and these never works without our IDs. So everyone prefer to use IDs as fragment identifiers for marking landmarks in the page instead of style hooks.

So, it&rsquo;s all about context. Never ban IDs from our project and use it for projects, if it is necessary.
