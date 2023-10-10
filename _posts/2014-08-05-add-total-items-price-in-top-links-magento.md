---
title: 'Add total items &#038; price in top links &#8211; Magento 1'
author: sarathlal
layout: post
tags:
  - Magento 1
---
In default, the Magento display total number of items as a part of my cart link in its top links.

Instead of this type top links, yesterday one of our client require total price & total items in there Magento shop top links.

In default, Magento utilize  addCartLink() Function in `Mage_Checkout_Block_Links` class for this purpose. Now we are going to update this class for our special use.

Editing  Magento core files is a bad idea. So first we copy the core file to our local code pool with same file structure.

First of all, copy `/app/code/core/Mage/Checkout/Block/Links.php` to `/app/code/local/Mage/Checkout/Block/`.

In that copied file, we can see two functions. Now we are going to edit   `addCartLink()` function on that file.

    
     public function addCartLink()
     {
     if ($parentBlock = $this->getParentBlock()) {
     $count = $this->helper('checkout/cart')->getSummaryCount();
    
     if( $count == 1 ) {
     $text = $this->__('%s Item', $count);
     } elseif( $count > 0 ) {
     $text = $this->__('%s Items', $count);
     } else {
     $text = $this->__('0 Items');
     }
    
     $grandTotal = $this->helper('checkout/cart')->getQuote()->getGrandTotal();
     $text .= $this->__(' - %s', $this->helper('core')->formatPrice($grandTotal, false));
     $parentBlock->removeLinkByUrl($this->getUrl('checkout/cart'));
     $parentBlock->addLink($text, 'checkout/cart', $text, true, array(), 100, null, 'class="top-link-cart"');
     }
     return $this;
     }
    

We just add some additional code in that function with the help of Magento helper class. In the next reload, we can see total price and cart items in our top links.
