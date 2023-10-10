---
title: Random banner in Magento 1 using static blocks
author: sarathlal
layout: post
tags:
  - Magento 1
---
The banners are an inevitable part of any E-Commerce store. They help to increase our sales by promoting new products, special offers & discounts etc.

Today I&#8217;m going to make a simple random banner in our Magento powered online store with static blocks and template files.

*   To add a random banner in Magento stores, first add few static blocks from administration panel (CMS->Static Blocks->Add new block).
*   When creating this static block, follow a common Identifier naming scheme for all these static block like


		BannerIdentifier_1
		BannerIdentifier_2
		BannerIdentifier_3
		BannerIdentifier_4
		...
		BannerIdentifier_N

*   Normally we use images as banner & so insert our banner image on each static block.
*   Then wrap that image using anchor tag that target our specific page, product or category like 

		<a href="http://mystore.com/my_new_product/"><img src="" alt="Some alt text"  /></a>

*   Now we just added an image link as our banner. But we have option to add text, buttons etc on that image with some CSS tricks & now that is purely off topic for me.
*   Then add a single line of code in our template file to echo a random static block.

		<?php echo $this->getLayout()->createBlock('cms/block')->setBlockId('BannerIdentifier_'.mt_rand(1, N))->toHtml() ?>

Here we use a PHP function, `mt_rand()` to achieve our goal. The `mt_rand()` return a random integer value between one and N because our parameters for `mt_rand()` function is one & N.

We use this returned integer value as a part of our static block identifier & echo that static block on that page.

To view our random banner, flesh the Magento cache and reload the store.
