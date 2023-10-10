---
title: 'Move right sidebar cart in to left using local.xml &#8211; Magento 1'
author: sarathlal
layout: post
tags:
  - Magento 1
---
In Default, Magento themes have a my cart block in right sidebar. If you wish to move it in to left, we can use `local.xml` file in layout.

    <?xml version="1.0" encoding="UTF-8"?>
    <layout>
     <default>
     <reference name="left">
     <block type="checkout/cart_sidebar" name="cart_sidebar" template="checkout/cart/sidebar.phtml" before="-">
     </block>
     </reference>
     <reference name="right">
     <action method="unsetChild"><name>cart_sidebar</name></action>
     </reference>
     </default>
    </layout>
    

Here first we added a cart sidebar in left column using reference name **left** and then remove default cart sidebar from right column using action method **unsetChild** as shown above.

If you wish to remove cart sidebar from right column, just remove that block using <strong style="font-weight: bold;">unsetChild</strong> in `local.xml`.

	<?xml version="1.0" encoding="UTF-8"?>
	<layout>
	 <default>
	 <remove name="cart_sidebar" />
	 </default>
	</layout>
