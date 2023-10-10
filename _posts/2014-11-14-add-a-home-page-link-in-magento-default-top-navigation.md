---
title: Add a home page link in Magento 1 default top navigation
author: sarathlal
layout: post
tags:
  - Magento 1
---
When customizing Magento themes, regularly I want to add a home page link on Magento top navigation.

We can easily add this home page link in default navigation by adding a single line of code in our template file.

First we want to find out the template file that render our top navigation. We can find the path of this template file by enabling Template Path Hints on Configuration >> Developer >> Debug section from admin interface.

Then add below code snippet in that file in the main UL or OL element inside the main nav element.

	<!-- ALTERNATIVE HOME BUTTON HACK -->
	<li class="home"><a href="<?php echo $this->getUrl('')?>"><?php echo $this->__('Home') ?></a></li>
	<!-- ALTERNATIVE HOME BUTTON HACK -->


Then save the file, refresh the cache and reload page again. We can see our new home page link in Mgento default top navigation.
