---
title:  Switch Magento 2 environment mode
layout: post
tags:
  - Magento 2
---

The Magento 2 have 3 main environment modes.

1. Default Mode - After fresh installation, if there is no other modes are not specified, our Magento 2 will be in default mode
2. Developer mode - During development & customization, we have to use Developer mode
3. Production mode - When we deploy our Magento installation to a production server, it must be production mode

The difference and details are avilable in the [Magento Dev Doc](http://devdocs.magento.com/guides/v2.0/config-guide/bootstrap/magento-modes.html){:target="_blank"}.

### Know the current mode

	magento deploy:mode:show

### Swich between Magento mode

I believe that your current directory is Magento installation root folder. If so, the command will be, 

	magento deploy:mode:set {mode}

##### Example - Switch to production mode

	bin/magento deploy:mode:set production

##### Example - Switch to Developer mode

First delete the contents of the `var/generation` and `var/di` directories.

	rm -rf var/di/* var/generation/*

Thedn switch mode

	bin/magento deploy:mode:set developer

Note: We cannot currently change from either developer or production mode to default mode. Unless we specify developer / production mode, Magento installation will be in default mode.
