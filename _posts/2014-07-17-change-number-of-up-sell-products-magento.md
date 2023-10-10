---
title: 'change number of up-sell products - Magento 1'
author: sarathlal
layout: post
tags:
  - Magento 1
---
To change number of up-sell products in Magento product detail page, change limit & column count in \`catalog.xml\` layout file in the following line.

	<block type="catalog/product_list_upsell" name="product.info.upsell" as="upsell_products" template="catalog/product/list/upsell.phtml">
	<action method="setColumnCount"><columns>4</columns></action>
	<action method="setItemLimit"><type>upsell</type><limit>4</limit></action>
	</block>
