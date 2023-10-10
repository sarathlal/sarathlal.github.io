---
title: User friendly product availability message in Magento 1
author: sarathlal
layout: post
tags:
  - Magento 1
---
In default, Magento never display out of stock products in store view. But we can enable this option from **System >> Configuration >> Inventory (Catalog) >> Stock options**.

If we enabled this option, the Magento store display all out of stock product in store view with Out of stock as Avilability.

Today, I&#8217;m going to make it as more user friendly. I wish to add an additional text to inform that visitors can call or contact me to know more about availability in such situations.

we have different way to achieve this additional text on low stock product. Just we want to check that the product is in out of stock & if so, echo our additional text.

Either we can edit single product view template file ( `yourtemplate/catalog/product/view.phtml` ) or file that caused for product availability mesage (`yourtemplate\catalog\product\view\type\availability\default.phtml`).

	<?php // Check to see if the item is in stock
	if($_product->stock_item->is_in_stock <= 0): ?>
	 <strong><a href="<?php echo Mage::getBaseUrl(Mage_Core_Model_Store::URL_TYPE_WEB) ?>contacts/" title="<?php echo $this->__('Email') ?>"><?php echo $this->__('Email') ?></a></strong>
	 <?php echo $this->__('or Call for Availability') ?> 1-222-333-444
	<?php endif; ?>
