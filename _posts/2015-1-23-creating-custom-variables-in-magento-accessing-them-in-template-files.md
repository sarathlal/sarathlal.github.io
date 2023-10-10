---
title: Creating custom variables in Magento 1 & accessing them in template files
author: sarathlal
layout: post
tags:
  - Magento 1
---
To create new custom variable in Magento store, first go to *System* >> *Custom Variable* from Magento dashboard.

Then create a new variable with Variable code, Variable name, Variable HTML Value and Variable Plain Value. Then save this new variable.

To access this custom variables, use below line of codes in Magento template files.

	// To get the TEXT value of the custom variable:
	Mage::getModel('core/variable')->setStoreId(Mage::app()->getStore()->getId())->loadByCode('custom_variable_code')->getValue('text');
	 
	// To get the HTML value of the custom variable:
	Mage::getModel('core/variable')->setStoreId(Mage::app()->getStore()->getId())->loadByCode('custom_variable_code')->getValue('html');
