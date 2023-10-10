---
title: 'Display top level categories & sub categories from template files - Magento 1'
author: sarathlal
layout: post
tags:
  - Magento 1
---
To display all top level categories and its sub categories from template file, we can use a code snippet in Magento.

	<?php $_helper = Mage::helper('catalog/category') ?>
	<?php $_categories = $_helper->getStoreCategories() ?>
	<?php $currentCategory = Mage::registry('current_category') ?>
	<?php if (count($_categories) > 0): ?>
		<ul>
			<?php foreach($_categories as $_category): ?>
				<li>
					<a href="<?php echo $_helper->getCategoryUrl($_category) ?>">
						<?php echo $_category->getName() ?>
					</a>
					<?php $_category = Mage::getModel('catalog/category')->load($_category->getId()) ?>
					<?php $_subcategories = $_category->getChildrenCategories() ?>
					<?php if (count($_subcategories) > 0): ?>
						<ul>
							<?php foreach($_subcategories as $_subcategory): ?>
								<li>
									<a href="<?php echo $_helper->getCategoryUrl($_subcategory) ?>">
										<?php echo $_subcategory->getName() ?>
									</a>
								</li>
							<?php endforeach; ?>
						</ul>
					<?php endif; ?>
				</li>
			<?php endforeach; ?>
		</ul>
	<?php endif; ?>
