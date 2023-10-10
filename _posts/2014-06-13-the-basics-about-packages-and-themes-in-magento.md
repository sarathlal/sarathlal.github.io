---
title: The basics about packages and themes in Magento 1
author: sarathlal
layout: post
tags:
  - Magento 1
---
When I begin Magento customization, some terms are little confusing for me. In my first day, I can&#8217;t understand the use of packages with the themes in Magento stores.

Actually I consumed a whole day to find its practical use & understand the flexibility of Magento themes.

The package is a collection of themes that determines the visual output and front-end functionalities of our Magento store. A package can be assigned on either the website-level and/or store view-level through the administration panel.

A theme is any combination of layout, template, locale and/or skin file(s) that create the visual experience.

A theme consists of any or all of the following:

*   Layout (located in app/design/frontend/our*package/our*theme/layout/)

These are basic XML files that define block structure for different pages as well as control META information and page encoding.

*   Templates (located in app/design/frontend/our*package/our*theme/template/)

These are PHTML files that contain (X)HTML markups and any necessary PHP tags to create logic for visual presentation.

*   Locale (located in app/design/frontend/our*package/our*theme/locale/)

These are simple text documents organized on a per language basis that contain translations for store copy.

*   Skins (located in skin/frontend/our*package/our*theme/skins)

These are block-specific Javascript, CSS and image files that compliment our (X)HTML.

**The default & non-default theme**

The Magento is built with the capacity to load multiple themes at once from a package. Also each and every package comes with a default theme.

The default theme is the main theme for a package. It have basic functionality & styles for an E-Commerce store.

If we like to customize our Magento store, we can create a non-default theme & then assign it to our store. 

By this way, the basic styles and functionality of our store will comes from default theme & our custom styles and functionality will comes from our non default themes.

If we assigned a non-default theme to our store, the application first look template files and skins files from that non default theme. If our non-default theme lack these file, the application automatically look files from default theme.
