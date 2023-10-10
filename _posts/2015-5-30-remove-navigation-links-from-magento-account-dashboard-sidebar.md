---
title:  Remove navigation links from Magento 1 account dashboard sidebar
layout: post
tags:
  - Magento 1
---

When we login as a user in a Magento site, we can see too many navigation links on the Account dashboard side bar. Some of them are unnecessary for simple E-Commerce projects and regularly I want to remove them.

To simply remove navigation links on the account dashboard side bar, we just want to over ride a template file.

**Step 1:** Select the template file ( yourPackage/YourTemplate/customer/account/navigation.phtml ).

**Step 2:** Replace the below line

	<?php $count = count($links); ?>

With
    
	<?php $_count = count($_links);
      unset($_links['account']); /* Account Info */     
      unset($_links['account_edit']); /* Account Info */            
      unset($_links['tags']); /* My Tags */
      unset($_links['invitations']); /* My Invitations */
      unset($_links['reviews']);  /* Reviews */
      unset($_links['wishlist']); /* Wishlist */
      unset($_links['newsletter']); /* Newsletter */
      unset($_links['orders']); /* My Orders */
      unset($_links['address_book']); /* Address */
      unset($_links['enterprise_customerbalance']); /* Store Credit */
      unset($_links['OAuth Customer Tokens']); /* My Applications */
      unset($_links['enterprise_reward']); /* Reward Points */
      unset($_links['giftregistry']); /* Gift Registry */
      unset($_links['downloadable_products']); /* My Downloadable Products */
      unset($_links['recurring_profiles']); /* Recurring Profiles */
      unset($_links['billing_agreements']); /* Billing Agreements */
      unset($_links['enterprise_giftcardaccount']); /* Gift Card Link */
	?>

The above code will unset all navigation links on Account dashboard side bar. That means, only unset the items you don't required.
