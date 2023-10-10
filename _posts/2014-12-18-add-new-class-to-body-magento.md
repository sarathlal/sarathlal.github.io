---
title: Add new class to body via local.xml file – Magento 1
author: sarathlal
layout: post
tags:
  - Magento 1
---
In Magento customizations, if you like to add a new class for body element in our Magento store, we can use a small code snippet in our theme’s local.xml file.

	 <default>
	 <reference name="root">
	 <action method="addBodyClass"><classname>my-class</classname></action>
	 </reference>
	 </default>

The above code will add a new class – `my-class` to body elements on all pages.

If you like to add this new body class for only specific pages like CMS pages or Category layered navigation pages, use there own page handle instead of default page handle.
