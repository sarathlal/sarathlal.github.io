---
title: Redirect to last added product category page from continue shopping button on cart page - Magento 1
author: sarathlal
layout: post
tags:
  - Magento 1
---

In default, if we click on continue shopping link on Magento cart page, it will redirect to last added product page. But there is no sense on this nature because we come back to an already added product page.

So today, we are going to modify this continue shopping link on cart page. After setup this option, when a user click on continue shopping button on cart page, he will be redirected to last added product's category page.

To do so, first we want to add below code in `app/design/frontend/yourpackage/yourtheme/template/checkout/cart.phtml` file.

	<?php
		$lastProductAddedToCartId = Mage::getSingleton('checkout/session')->getLastAddedProductId();
		if($lastProductAddedToCartId) {
			$productCategoryIdsArray = Mage::getModel('catalog/product')->load($lastProductAddedToCartId)->getCategoryIds();
			$continueShoppingCategoryUrl = Mage::getModel('catalog/category')->load($productCategoryIdsArray[0])->getUrl();
		}
	?>

Then edit continue shopping button on the same file with our new variables.

	<?php if($this->getContinueShoppingUrl()): ?>
		<button type="button" title="<?php echo $this->__('Continue Shopping') ?>" class="button2 btn-continue" onclick="setLocation('<?php echo (isset($continueShoppingCategoryUrl)) ? $continueShoppingCategoryUrl : $this->getContinueShoppingUrl(); ?>')"><span><span><?php echo $this->__('Continue Shopping') ?></span></span></button>
	<?php endif; ?>

Then after reindex Magento files and refresh cache. Thats enough.

In the above code, we choosed first category from the array of all category of selected product. If you like to target last category from the category array of that product, we can simply tweake the code like below one.

	<?php
		$lastProductAddedToCartId = Mage::getSingleton('checkout/session')->getLastAddedProductId();
		if($lastProductAddedToCartId) {
			$productCategoryIdsArray = Mage::getModel('catalog/product')->load($lastProductAddedToCartId)->getCategoryIds();
			$continueShoppingCategoryUrl = Mage::getModel('catalog/category')->load(end($productCategoryIdsArray)->getUrl();
		}
	?>
