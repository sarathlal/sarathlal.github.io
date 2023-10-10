---
title: Different user related URL for template files in Magento 1
author: sarathlal
layout: post
tags:
  - Magento 1
---
To display user related links like login, logout & registration etc, we can simply use default `customer` helper class in template files.

	<?php
	$helper = Mage::helper("customer"); // gets Mage_Customer_Helper_Data

	echo  $helper->getAccountUrl();//Account URL
	echo  $helper->getRegisterUrl();//New Registration URL
	echo  $helper->getLoginUrl();//Login URL
	echo  $helper->getLogoutUrl();//Logout URL
	echo  $helper->getEditUrl();//Edit account URL
	echo  $helper->getForgotPasswordUrl();//Forget password  URL
	?>

Here I just echo different URL from template files. To make it as links, we want to use them with HTML anchor tag.
