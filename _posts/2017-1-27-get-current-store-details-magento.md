---
title:  Get current store details - Magento 1
layout: post
tags:
  - Magento 1
---

	// Gets the current store's details
	$store = Mage::app()->getStore();
	 
	// Gets the current store's id
	$storeId = Mage::app()->getStore()->getStoreId();
	 
	// Gets the current store's code
	$storeCode = Mage::app()->getStore()->getCode();
	 
	// Gets the current website's id
	$websiteId = Mage::app()->getStore()->getWebsiteId();
	 
	// Gets the current store's group id
	$storeGroupId = Mage::app()->getStore()->getGroupId();
	 
	// Gets the current store's name
	$storeName = Mage::app()->getStore()->getName();
	 
	// Gets the current store's sort order
	$storeSortOrder = Mage::app()->getStore()->getSortOrder();
	 
	// Gets the current store's status
	$storeIsActive = Mage::app()->getStore()->getIsActive();
	 
	// Gets the current store's locale
	$storeLocaleCode = Mage::app()->getStore()->getLocaleCode();
	 
	// Gets the current store's home url
	$storeHomeUrl = Mage::app()->getStore()->getHomeUrl();
