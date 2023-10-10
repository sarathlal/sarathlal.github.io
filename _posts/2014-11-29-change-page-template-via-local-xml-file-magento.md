---
title: 'Change page template via local.xml file &#8211; Magento 1'
author: sarathlal
layout: post
tags:
  - Magento 1
---
If we like to change default page templates in Magento for different pages, we can use `local.xml` file in our theme&#8217;s layout folder.

     <handle>
     <reference name="root">
     <action method="setTemplate"><template>page/your_page_name.phtml</template></action>
     </reference>
     </handle>

####  Example

     <catalog_category_default translate="label">
     <reference name="root">
     <action method="setTemplate"><template>page/1column.phtml</template></action>
     </reference>
     </catalog_category_default>

This code will make Magento default catalog category ( Non-Anchor ) page template as `1coloumn.phtml`.
