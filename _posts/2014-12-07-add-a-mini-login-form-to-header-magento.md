---
title: Add a mini login form to header – Magento 1
author: sarathlal
layout: post
tags:
  - Magento 1
---
In default, Magento have a mini login form and we can use it any where in our page blocks.

Now I’m going to add this mini login form in our page header with in few simple steps.

First we want to add login form block to header for sign out customers. We can use our theme’s `local.xml` file for this purpose.

Just add below code snippet to our theme’s `local.xml` file.

	 <customer_logged_out>
	 <reference name="header">
	 <block type="customer/form_login" name="header_customer_form_mini_login" template="customer/form/mini.login.phtml"/>
	 </reference>
	 </customer_logged_out>
	 
Then call this login form in header section of our template file.

	 <?php echo $this->getChildHtml('header_customer_form_mini_login') ?>

This code snippets will display a login form in header section for logged out customers only.
