---
title: The basics of Magento 1 template hierarchy
author: sarathlal
layout: post
tags:
  - Magento 1
---
To render web pages, the Magento use different files available from different themes and packages. It is known as template hierarchy.

The Magento has always used fall-back logic in rendering themes. The fall-back logic means, to render a web page, first it look for file in current theme & if it is absent at there, it utilize the file from default theme in current package. 

From Magento CE v1.4 and EE v1.8, the base package is the final cross-package fall-back point. That means, files from base package is the last fall-back option to render web page & so base package consist with all core Magento functionality.

The fall-back hierarchy from Magento CE v1.4+ and EE v1.8+ is as follows.

First look for requested file in:

	app/design/frontend/custom_package/custom_theme/

	skin/frontend/custom_ package/custom_theme

If not found, then look for requested file in:

	app/design/frontend/custom_package/default

	skin/frontend/custom_package/default

If not found, last look for requested file in:

	app/design/frontend/base/default

	skin/frontend/base/default

If not found, a rendering error will occur.

As an example, consider that our custom theme calls for a CSS file called `styles.css` to render a web page. If the Magento is unable to find the file in our custom theme, it will go to the default theme in current package. Should this fail, it will go to use `style.css` file from base theme.

If we can use this fall-back logic in theme hierarchy as effectively, we just want to edit and maintain only the files require to change as a custom theme and all of the other functionality will be captured from either the custom package default theme or the base package.
