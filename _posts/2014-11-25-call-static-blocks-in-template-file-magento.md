---
title: 'Call static blocks in template file &#8211; Magento 1'
author: sarathlal
layout: post
tags:
  - Magento 1
---
To call static blocks created in Magento admin panel, we can use below code snippet.

    <?php echo $this->getLayout()->createBlock('cms/block')->setBlockId('our_block_identifier')->toHtml(); ?>
