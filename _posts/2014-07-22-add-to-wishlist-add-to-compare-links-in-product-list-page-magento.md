---
title: 'Add to wishlist &#038; Add to compare links in product list page - Magento 1'
author: sarathlal
layout: post
tags:
  - Magento 1
---
To display `add to wishlist` link & `add to compare` link on my Magento product list pages, I used below lines of codes in template files for product lists.

###  Add to Wishlist link

	<a href="<?php echo $this->helper('wishlist')->getAddUrl($_product) ?>" class="link-wishlist"><?php echo $this->__('Add to Wishlist') ?></a>

###  Add to Compare link

	<a href="<?php echo $_compareUrl ?>" class="link-compare"><?php echo $this->__('Add to Compare') ?></a>
