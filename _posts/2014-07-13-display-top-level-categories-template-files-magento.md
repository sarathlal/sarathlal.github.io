---
title: Display top level categories from template files - Magento 1
author: sarathlal
layout: post
tags:
  - Magento 1
---
In E-commerce websites, normally they have a wide variety of products on different categories. So these categories have a huge impact on user interaction.

To display top level categories in Magento stores, we can use a simple code snippet that utilize helper class in template files.

	<ul>
		 <?php $helper = $this->helper('catalog/category') ?>
		 <?php foreach ($helper->getStoreCategories() as $_category): ?>
			 <li><a href="<?php echo Mage::getModel('catalog/category')->setData($_category->getData())->getUrl(); ?>" title="<?php echo $_category->getName() ?>"><?php echo $_category->getName() ?></a></li>
		 <?php endforeach ?>
	</ul>
