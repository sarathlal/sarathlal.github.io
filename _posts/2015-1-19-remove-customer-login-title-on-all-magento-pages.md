---
title: Remove customer login title on all Magento 1 pages
author: sarathlal
layout: post
tags:
  - Magento 1
---
When dealing with Magento login form in custom themes, often our all page title will become “Customer login”.

We can easily solve this issue by editing a Magento core file.

To do so, first we want to copy `Login.php` file from `app/code/core/Mage/Customer/Block/Form/` and paste this file in our local code pool with same directory structure like `app/code/local/Mage/Customer/Block/Form/Login.php`.

In that file, we can see that there is protected function \_prepareLayout. In that function, we have a `setTitle` method in a line.

	 protected function _prepareLayout()
	 {
	 $this->getLayout()->getBlock('head')->setTitle(Mage::helper('customer')->__('Customer Login'));
	 return parent::_prepareLayout();
	 }

Now we just want to comment out this line & that is enough.

	 protected function _prepareLayout()
	 {
	 //$this->getLayout()->getBlock('head')->setTitle(Mage::helper('customer')->__('Customer Login'));
	 return parent::_prepareLayout();
	 }

Then reindex data, refresh the cache and reload the store view page again.
