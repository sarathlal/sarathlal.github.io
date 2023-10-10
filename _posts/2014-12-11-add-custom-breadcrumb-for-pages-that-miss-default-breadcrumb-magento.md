---
title: Add custom breadcrumb for pages that miss default breadcrumb – Magento 1
author: sarathlal
layout: post
tags:
  - Magento 1
---

In default, Magento don’t have breadcrumb for some of its pages like shopping cart etc. In such situations, we can add a custom breadcrumb for such pages.

First we want to make a template file for below code snippet and then call it in other pages that do'nt have a default breadcrumb. That is enough.

	<?php 
	/**
	 *
	 * CUSTOM BREADCRUMBS
	 *
	 * Adds url breadcrumbs for pages that do not have breadcrumbs by default
	 *
	 */
	 
	?>
	<?php if(is_null($crumbs)): ?>
	<?php 
	 
	/**
	 * NOTE
	 * On some servers use ->getServer('PATH_INFO')
	 * and on some ->getServer('ORIG_PATH_INFO')
	 */
	 
	$urlRequest = Mage::app()->getFrontController()->getRequest();
	$urlPart = $urlRequest->getServer('ORIG_PATH_INFO');
	 
	if(is_null($urlPart))
	{
	 $urlPart = $urlRequest->getServer('PATH_INFO');
	}
	 
	 
	$urlPart = substr($urlPart, 1 );
	$currentUrl = $this->getUrl($urlPart);
	 
	//$controllerName = Mage::app()->getFrontController()->getRequest()->getControllerName();
	//$controllerName = ucfirst($controllerName);
	 
	$controllerName = str_replace("/", " ", $urlPart);
	$controllerName = str_replace("_", " ", $controllerName);
	$controllerName = str_replace("-", " ", $controllerName);
	$controllerName = ucfirst($controllerName);
	 
	?>
	<span class="breadcrumbs">
	<strong class="float"><?php echo $this->__("You're currently on: ") ?></strong>
	<ul class="breadcrumbs">
	<li class="home">
	 <a title="<?php echo $this->__('Go to Home Page') ?>" href="<?php echo $this->getUrl() ?>"><?php echo $this->__('Home') ?></a>
	 </li>
	 <li> / </li>
	 <li class="<?php echo strtolower($controllerName) ?>">
	 <strong><?php echo $this->__($controllerName) ?></strong>
	 </li>
	</ul>
	</span>
	<?php endif; /* END OF CUSTOM BREADCRUMBS */ ?>

In my Magento installation, first I create a new php file `cstm_brdcrmb.php` with the above code snippet in `app/design/frontend/my_package/my_theme/template/page/html/` and then call it in other pages.

	<?php echo $this->getLayout()->createBlock('core/template')->setTemplate('page/html/cstm_breadcrumb.phtml')->toHtml(); ?>

**The above code is first published in [Inchoo](http://inchoo.net/magento/programming-magento/add-breadcrumbs-in-magento-to-pages-that-dont-have-them/) blog.**
