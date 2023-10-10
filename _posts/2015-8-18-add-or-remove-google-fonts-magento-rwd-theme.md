---
title:  Add or remove Google fonts in RWD theme - Magento 1.9
layout: post
tags:
  - Magento 1
---

Add below code snippet inside correct page handle & reference to add or remove google fonts from Magento

### Remove default Raleway font from Magento default RWD theme

	<action method="removeItem"><type>link_rel</type><name>//fonts.googleapis.com/css?family=Raleway:300,400,500,700,600</name></action>
			
### Add new fonts in theme
			
	<action method="addLinkRel">
		<rel>stylesheet</rel>
		<href>//fonts.googleapis.com/css?family=Lato:300,400,700</href>
	</action>

