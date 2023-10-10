---
title: 'Service Temporarily Unavailable &#8211; Disable maintenance mode in Magento 1'
author: sarathlal
layout: post
tags:
  - Magento 1
---
If you’re seeing the **Service Temporarily Unavailable** screen when you attempt to load your Magento store, the most likely cause is you&#8217;ve made some updates on Magento recently, and the `maintenance.flag` file in your Magento root directory wasn&#8217;t successfully removed by the Magento Connect tool.

To fix this issue, just go to root folder of Magento installation & remove `maintenance.flag` file from there. Also remove all cache files from `var/cache`.

Then reload your Magento store.

The `maintenance.flag` file can be triggered by running updates or installations of extensions in Magento Connect. This file will be automatically removed on successful completion of the upgrade or installation. But in some special occasions, it fails due to some reasons & we will see this screen.
