---
title: Add to cart button in related products on product detail page - Magento 1
author: sarathlal
layout: post
tags:
  - Magento 1
---
If you like to add a `Add to Cart` button on related products in product detail pages with quantity input box, first open the Magento template file that caused for related product list on product detail page.

In Magento, the `related.phtml` file located in `app/design/frontend/your_package/your_theme/template/catalog/product/list/` was generate the related product list on product page.

Then we want to add a new form with submission button & quantity input field inside the loop that generate related products.

	<form action="<?php echo $this->getAddToCartUrl($_item) ?>" method="post" id="product_addtocart_form_<?php echo $_item->getId()?>"<?php if($_item->getOptions()): ?> enctype="multipart/form-data"<?php endif; ?>> 
		<?php if(!$_item->isGrouped()): ?> 
			<input type="text" name="qty" id="qty" maxlength="12" value="<?php echo ($this->getMinimalQty($_item)?$this->getMinimalQty($_item):1) ?>" /> 
			<label for="qty"><?php echo $this->__('Qty') ?>:</label> 
		<?php endif; ?> 
		<button type="button" onclick="this.form.submit()"><span><span><span><?php echo $this->__('Add to Cart') ?></span></span></span></button>
	</form>

Save the `related.phtml` file, flush the Magento cache & reload our product detail page. We can see a new `Add to Cart` button with quantity input box on related products on product detail pages.
