---
title: 'Replace filter links in layered navigation with checkbox &#8211; Magento 1'
author: sarathlal
layout: post
tags:
  - Magento 1
---
The layered navigation in Magento help to filter products with in catelog with attributes, price & categories etc.

In default layered navigation, Magento use anchor link to filter products. Yesterday, I want to make checkbox instead of these anchor links.

Makeing checkbox from anchor link is too easier than I think. I just want to add a checkbox in a form and then add an onclick event for this check box to consume my target link.

That means, we want to change few lines of code in `app/design/frontend/ourpackage/ourtheme/template/catalog/layer/filter.phtml`.

First find out lines of code that caused for that anchor links. Then make a form and checkbox using variables used in that anchor link. 

Your final code lines will look like below code snippet.

	<form>
	<span class="check-box"><input type="checkbox" name="vehicle" onclick='window.location.assign("<?php echo $this->urlEscape($_item->getUrl()) ?>")'/></span><span class="label"><?php echo $_item->getLabel() ?><span>
	</form>

Then remove that old anchor link & use our new checkbox in Magento layered navigation.
