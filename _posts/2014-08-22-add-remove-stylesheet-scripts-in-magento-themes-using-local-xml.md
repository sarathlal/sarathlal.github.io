---
title: 'Add or remove stylesheet &#038; scripts in Magento 1 themes using local.xml'
author: sarathlal
layout: post
tags:
  - Magento 1
---
To add and remove style sheet & scripts in Magento themes, we can simply use `local.xml` file in our theme layout folder.

	<handle>
	 <reference name="head">
	 
	 <action method="addJs"><script>prototype/prototype.js</script></action> <!-- adds a js referencing to the /js directory -->
	 
	 <action method="addCss"><stylesheet>css/custom.css</stylesheet></action> <!-- adds CSS looking at the skin/ directories ( in reverse order: base/default, default/default, default/yourtheme, yourpackage/yourtheme -->
	 
	 <action method="addItem"><type>skin_js</type><name>js/custom_script.js</name><params/></action> <!-- adds a js at the skin/ directories in the same manner as the above addCss directive -->

	 <action method="removeItem"><type>skin_js</type><name>scripts/functions.js</name></action><!--Remove JS from skin Folder-->
	 
	 <action method="removeItem"><type>skin_css</type><name>css/styles.css</name></action><!--Remove CSS from skin Folder-->
	 
	 <action method="removeItem"><type>js</type><name>scripts/functions.js</name></action><!--Remove JS from js Folder-->
	 
	 </reference>
	</handle>
