---
title: Display all products without pagination – Magento 1
author: sarathlal
layout: post
tags:
  - Magento 1
---

To display all products without pagination, we want to edit a core file in Magento.

To avoid feature update issues, first we are going to copy that core file in to our local code pool. So just copy `Toolbar.php` file from `app/code/core/Mage/Catalog/Block/Product/List/` to our local code pool with same directory structure.

Now our file will be available as `app/code/local/Mage/Catalog/Block/Product/List/Toolbar.php` and we are going to edit this file.

Inside this file, we can find a function `getLimit()`( beginning around line 723 ). In the beginning of that function, just change `$limit` variable value as `'all'`.

	$limit = 'all';

After reloading the page, now we can see all the products in a single page with out pagination in Magento. If you feel any missing, just re index all data and refresh the Magento cache and reload again.
