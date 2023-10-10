---
title: Add to cart button on upsell products in product detail page - Magento 1
author: sarathlal
layout: post
tags:
  - Magento 1
---
To add a `Add to Cart` button on upsell products in product detail pages, first open the `upsell.phtml` file located in `app/design/frontend/your_package/your_theme/template/catalog/product/list/` that caused for these upsell products list.

Then add a new form with `Add to Cart` button & quantity input box inside the loop that generate upsell products.

	<form action="<?php echo $this->getAddToCartUrl($_link) ?>" method="post" id="product_addtocart_form_<?php echo $_link->getId()?>"<?php if($_link->getOptions()): ?> enctype="multipart/form-data"<?php endif; ?>>
		<?php if(!$_link->isGrouped()): ?>
			<input type="text" name="qty" id="qty" maxlength="12" value="<?php echo ($this->getMinimalQty($_link)?$this->getMinimalQty($_link):20) ?>" />
			<label for="qty"><?php echo $this->__('Qty') ?>:</label>
		<?php endif; ?>
		<button type="button" onclick="this.form.submit()"><span><span><span><?php echo $this->__('Add to Cart') ?></span></span></span></button>
	</form>
