---
title: 'Display all product reviews on product page &#8211; Magento 1'
author: sarathlal
layout: post
tags:
  - Magento 1
---
To display product reviews on product page, first we want to edit `catalog.xml` found at `app/design/frontend/YourPackage/YourTheme/layout/catalog.xml`.

We want to add a new page block in `catalog_product_view` class. Inside this reference, add the following code:

	<block type="review/product_view_list" name="product.info.product_additional_data" as="product_review" template="review/product/view/list.phtml"></block>

Then we want to add a single line of code on the product page in `app/design/frontend/YourPackage/YourTheme/template/catalog/product/view.phtml` at appropriate place.

	<?php echo $this->getChildHtml('product_review') ?>

To view product reviews on product page, just flush the Magento cache after editing these files.
