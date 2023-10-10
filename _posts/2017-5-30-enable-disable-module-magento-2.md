---
title: Enable / Disable Magento 2 module using command line
layout: post
tags:
  - Magento 2
---

First we have to upload module files to our server.

Then check the current status of our modules.

	php bin/magento module:status

We can see the active & disabled module. On the bottom, we can see the disabled modules.

By default, the new module will be in disabled status. We have to enable & install them.

#### Enable a module.

	php bin/magento module:enable Vendor_Module

This command adds our module to the modules list in `app/etc/config.php`.

#### Install enabled modules

	php bin/magento setup:upgrade

#### Disable a module

	php bin/magento module:disable Vendor_Module

