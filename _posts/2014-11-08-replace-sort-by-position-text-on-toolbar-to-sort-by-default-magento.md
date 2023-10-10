---
title: 'Replace Sort by &#8220;Position&#8221; text on toolbar to Sort By &#8220;Default&#8221; &#8211; Magento 1'
author: sarathlal
layout: post
tags:
  - Magento 1
---
The Magento offer a neat toolbar in Catalog index pages to filter products with various options. In default, there is a sorting option according to varoius product attributes.

We can easily customize this sorting option in Toolbar from back end. We can add or remove product attribute for sorting by defining attribute scope and there visibility.

But Magento add a general sorting option, sort by &#8220;Position&#8221; in its toolbar. This is a wired setting for Magento newbies like me. But basically this sorting means, we can provide a number (position) for each product in back end and can sort product according to this number from toolbar.

But in my latest Magento customization, my client request to replace this Sort by &#8220;Position&#8221; with Sort by &#8220;Default&#8221;. They just want to change that text &#8220;Position&#8221; with &#8220;Default&#8221;. That is enough.

So to achieve this change, now we are going to edit core feature of Magento code. So to avoid update issues, first copy `Config.php` in `app\code\core\Mage\Catalog\Model\` to `app\code\local\Mage\Catalog\Model\` folder with same Directory structure.

Then replace

	$options = array(
	 'position' => Mage::helper('catalog')->__('Position')
	);

with

	$options = array(
	 'position' => Mage::helper('catalog')->__('Default')
	);

in `getAttributeUsedForSortByArray()` function.

This will replace text &#8220;Position&#8221; with &#8220;Default&#8221; in Sort by section in Magento toolbar.
