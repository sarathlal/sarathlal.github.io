---
title: Remove top links one by one in Magento 1 using local.xml file
author: sarathlal
layout: post
tags:
  - Magento 1
---
Just use below code snippet in theme’s local.xml file and it will remove all Magento top links one by one.

	 <default>
	 <reference name="root">
	 <reference name="top.links">
	 
	 <!-- Removes 'My Account' link -->
	 <action method="removeLinkByUrl"><url helper="customer/getAccountUrl"/></action>
	 
	 <!-- Removes 'Wishlist' link -->
	 <!-- for Magento 1.3.x -->
	 <action method="removeLinkByUrl"><url helper="wishlist/"/></action>
	 
	 <!-- for Magento 1.4.x -->
	 <remove name="wishlist_link"/>
	 
	 <!-- Removes 'My Cart' AND 'Checkout' links-->
	 <remove name="checkout_cart_link"/>
	 
	 <!-- To re-add 'My Cart' or 'Checkout' after removing both 
	 <block type="checkout/links" name="checkout_cart_link_custom">
	 <action method="addCartLink"></action>
	 <action method="addCheckoutLink"></action>
	 </block>
	 -->
	 
	 </reference>
	 </reference>
	 </default>
	 
	 <customer_logged_out>
	 <!-- Removes 'Log In' link -->
	 <reference name="top.links">
	 <action method="removeLinkByUrl"><url helper="customer/getLoginUrl"/></action>
	 
	 <!-- Remove Register link --> 
	 <action method="removeLinkByUrl"><url helper="customer/getRegisterUrl"/></action>
	 
	 </reference>
	 </customer_logged_out>

	 <customer_logged_in>
	 <!-- Removes 'Log Out' link-->
	 <reference name="top.links">
	 <action method="removeLinkByUrl"><url helper="customer/getLogoutUrl"/></action>
	 </reference>
	 </customer_logged_in>
