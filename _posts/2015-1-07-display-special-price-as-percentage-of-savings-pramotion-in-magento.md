---
title: Display special price as percentage of savings pramotion in Magento 1
author: sarathlal
layout: post
tags:
  - Magento 1
---

If we have products with special price in our Magento store, we can simply display the percentage of savings on this product in single product view page.

We can copy paste below code snippet in single product view template files. Before using, just ensure that we already loaded our product object.

	 <?php
	 // Get the Special Price FROM date
	 $specialPriceFromDate = Mage::getModel('catalog/product')->load($_product->getId())->getSpecialFromDate();
	 // Get the Special Price TO date
	 $specialPriceToDate = Mage::getModel('catalog/product')->load($_product->getId())->getSpecialToDate();
	 // Get Current date
	 $today = time();

	 $savingsDollarValue = ($_product->getPrice() - $_product->getFinalPrice());
	 $originalPrice = $_product->getPrice(); //get orginal price
	 $discountPrice = $_product->getFinalPrice(); //get the discount amount
	 $savings = $originalPrice - $discountPrice; //get the saving amount from orginal price - discount price
	 $savingsPercentage = round(($savings / $originalPrice) * 100, 0); //get discount Percentage
	 $productType = $_product->getTypeID();

		if ($savings):
		if ($today >= strtotime($specialPriceFromDate) && $today <= strtotime($specialPriceToDate) || $today >= strtotime($specialPriceFromDate) && is_null($specialPriceToDate)):
		?> 

			<p> <?php echo $this->__('EXTRA') ?><?php echo ' ' ?>
			<?php echo $this->getIdSuffix() ?> <?php echo $savingsPercentage, '%'; //display discount amount ?>
			<?php echo $this->__('Off') ?><?php echo ', ' ?><?php echo $this->__('untill') ?><?php echo ' ' ?>
			<?php echo $currentDate = Mage::getModel('core/date')->date('F dS', strtotime($specialPriceToDate)); ?>
			</p>

		<?php
		endif;
		endif;
	 ?>

The above code will display one line of text like below one in our product view page.

	EXTRA 30% off, until September 29th
