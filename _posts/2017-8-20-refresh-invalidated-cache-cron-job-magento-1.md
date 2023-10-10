---
title:  Refresh the invalidated cache using cron job - Magento 1
layout: post
tags:
  - Magento 1
---

In Magento, when we make changes in products, static blocks etc, to shows the changes on frontend, we have to refresh the invalidated cache from `System` > `Cache Management`.

This is a default functionality in Magento. But some new admin didn't care about cache management and argue that changes are not happen in front end.

Below you can find a PHP script that will refresh the invalidate cache types only.

	<?php
	ini_set('max_execution_time', 18000);
	require_once 'app/Mage.php';
	$app = Mage::app('admin');
	umask(0);
	Mage::setIsDeveloperMode(true);

	//Cache Refresh Start
	$invalidatedTypes = Mage::app()->getCacheInstance()->getInvalidatedTypes();
	foreach ($invalidatedTypes as $type) {
		Mage::app()->getCacheInstance()->cleanType($type->getId());
		Mage::log('Cache Type '.$type->getId()." Is Refresh.",null,'Refresh_Cache.log');
	}
	//Cache Refresh End

	?>

If you want to refresh invalidate cache at specific intervals,

1. Create a PHP file in your server.
2. Copy above code snippet in that file.
3. Create a cron job that run the new PHP file at a specific interval.

Here is my new cron job in a cPanel server.

![Refresh invalidate cache using cron job](/images/2017/cPanel-cron-job-refresh-invalidate-cache-types.png)



