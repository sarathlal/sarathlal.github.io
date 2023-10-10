---
title: Add Open Graph meta tags in Magento 1
author: 
layout: post
tags:
  - Magento 1
---

Now the Open Graph meta tags are consider as an essential part of webpage due to high impact of social media. Also these tags have few indirect impact on Search Engine Optimization.

Just copy and paste below codes in `head.phtml` file in our template file. The `head.phtml` file was located in `app/design/frontend/default/YOURTHEME/template/page/html/head.phtml`.

If you don't have a `head.phtml` file in your theme, copy one from base theme and use it in your own theme.

This code can go anywhere in the file but we usually put it before Magento outputs the theme CSS files, so before this line `<?php echo $this->getCssJsHtml() ?>`.

	<?php /* Open Graph Protocol for Facebook and SEO start here */ ?>
	<?php if(Mage::registry('current_product')): ?>
	 <?php $product = Mage::registry('current_product'); ?>
	 <meta property="og:title" content="<?php echo ($product->getName()); ?>" />
	 <meta property="og:type" content="product" />
	 <meta property="og:image" content="<?php echo $this->helper('catalog/image')->init($product, 'small_image')->resize(200,200);?>" />
	 <meta property="og:url" content="<?php echo Mage::registry('product')->getProductUrl(); ?>" />
	 <meta property="og:description" content="<?php echo strip_tags(($product->getShortDescription())); ?>" />
	 <meta property="og:site_name" content="<?php echo Mage::app()->getStore()->getName(); ?>" />
	 
	<?php elseif(Mage::registry('current_category')): ?>
	 <meta property="og:title" content="<?php echo $this->getTitle() ?>" />
	 <meta property="og:type" content="product.group" />
	 <meta property="og:url" content="<?php echo $this->helper('core/url')->getCurrentUrl();?>" />
	 <meta property="og:description" content="<?php echo strip_tags($this->getDescription()) ?>" />
	 <meta property="og:site_name" content="<?php echo Mage::app()->getStore()->getName(); ?>" />
	 
	<?php elseif((Mage::getSingleton('cms/page')->getIdentifier() == 'home' &&
	 Mage::app()->getFrontController()->getRequest()->getRouteName() == 'cms')) : ?>
	 <meta property="og:title" content="<?php echo $this->getTitle() ?>" />
	 <meta property="og:type" content="website" />
	 <meta property="og:url" content="<?php echo $this->helper('core/url')->getCurrentUrl();?>" />
	 <meta property="og:description" content="<?php echo strip_tags($this->getDescription()) ?>" />
	 <meta property="og:site_name" content="<?php echo Mage::app()->getStore()->getName(); ?>" />
	 
	<?php else: ?>
	 <meta property="og:title" content="<?php echo $this->getTitle() ?>" />
	 <meta property="og:type" content="article" />
	 <meta property="og:url" content="<?php echo $this->helper('core/url')->getCurrentUrl();?>" />
	 <meta property="og:description" content="<?php echo strip_tags($this->getDescription()) ?>" />
	 <meta property="og:site_name" content="<?php echo Mage::app()->getStore()->getName(); ?>" />
	<?php endif; ?>
	<?php /* Open Graph Protocol for Facebook and SEO end here */ ?>
