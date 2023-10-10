---
title: Brief about Magento 2 cache commands
layout: post
tags:
  - Magento 2
---

### Check current status of Magento 2 cache

	php bin/magento cache:status

If cache is enabled, the result will be

![magento-2-store-configuration](/images/2017/cache-status-magento-2.png)

If cache is disabled, the values will be 0.

### Clean cache

	php bin/magento cache:clean

### Flush cache

	php bin/magento cache:flush

### Disable cache

	php bin/magento cache:disable


### Disable specific cache

	php bin/magento cache:disable CACHE_TYPE

**Example**

	php bin/magento cache:disable config

### Enable Cache

	php bin/magento cache:enable

### Enable specicfic cache

	php bin/magento cache:enable CACHE_TYPE

**Example**

	php bin/magento cache:enable layout

