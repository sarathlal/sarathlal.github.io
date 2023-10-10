---
title: Enable template path hints in Magento 1 front end
author: sarathlal
layout: post
tags:
  - Magento 1
---
The Magento utilize hundred of files from themes and packages to render web pages. So when doing customization in Magento theme, it is too hard to understand which template file that generate a block of content.

However, there is a neat option to display file path which cause for rendered block of data. We just want to enable `Template Path Hints` in back end.

To enable this developer option,

1.  Login to the your Magento as Admin.
2.  Select settings from System > Configuration.
3.  Under Current Configuration Scope at top, select Default Store View or the Name of the web store you&rsquo;ve defined.
4.  On the left Pane, select the Developer Tab.
5.  In Developer Tab, under the Debug section, there is an option to enable Template Path Hints.

After saving the Configuration, the front end will show boxes with red border with the path of the template file, which cause for that particular content block.
