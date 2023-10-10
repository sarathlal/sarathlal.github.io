---
title: Enable or disable maintance mode - Magento 2
layout: post
tags:
  - Magento 2
---

The Magento application have option to make site in maintance mode during maintaining, upgrading, or reconfiguring our site.

Magento detects maintenance mode as follows:

If `var/.maintenance.flag` does not exist, maintenance mode is off and Magento operates normally. Otherwise, maintenance mode is on unless `var/.maintenance.ip` exists:

The `var/.maintenance.ip` can contain a list of IP addresses. If an entry point is accessed using HTTP and the client IP address corresponds to one of the entries in that list, then maintenance mode is off.

### Add allowed IP during maintanace mode

	php bin/magento maintenance:allow-ips xxx.xxx.xxx.xxx

### Enable maintanace mode

	php bin/magento maintenance:enable

### Disable maintance mode

	php bin/magento maintenance:disable
