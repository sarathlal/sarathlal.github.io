---
title: 'Display breadcrumb on any template file &#8211; Magento 1'
author: sarathlal
layout: post
tags:
  - Magento 1
---
The breadcrumbs are consider as a major navigational aid in web applications. In E-Commerce websites, the breadcrumbs have a major role in user navigation.

To display a breadcrumb from any template file in Magento, we just want to echo default breadcrumb block.

	<?php echo $this->getLayout()->getBlock('breadcrumbs')->toHtml(); ?>

After adding the above code line in any template file, flush the Magento cache & reload our page. We can see a nice default Magento breadcrumb in our web page.
