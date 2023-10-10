---
title: 'Display login and logout links from template file - Magento 1'
author: sarathlal
layout: post
tags:
  - Magento 1
---
In some special cases, we want to display login & logout links in some specific areas of our Magento themes. In such situations, we can use a simple code snippet on our template files.

	<?php
	//check the user is logged in or not
	if (! Mage::getSingleton('customer/session')->isLoggedIn()){
		//if user logged on show the logout link
		echo "<a href="". Mage::helper('customer')->getLoginUrl() . "">" . "Login" . "</a>";
	}
	else{
		//if user is not logged on yet show the login link
		echo "<a href="". Mage::helper('customer')->getLogoutUrl() . "">" . "Logout" . "</a>";
	}
	?>
