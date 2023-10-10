---
title: 'Add an Add to cart button outside a product page &#8211; WooCommerce'
author: sarathlal
layout: post
tags:
  - WooCommerce
  - WordPress
---
If you like to promote a WooCommerce product in our WordPress post or article, display an add to cart button for that product on that post or article is always a good option.

We can use a WooCommerce short code for this purpose.

When a user click on that add to cart button, instead of directing the user to the product page, we can add the product to his cart from the post / article as it reduce an unnecessary step.

###  Step 1 – Get Product Details

*   First login to WordPress dashboard & then navigate to Products.
*   In product list, we can see there product ID below each product.
*   Note down one of the product ID.

###  Step 2 – Insert the Add-to-Cart Short code

*   Navigate to the post / page / article in which you want to add the cart button and click in the text editor wherever you want to display the add-to-cart button.
*   In some WordPress version, there is a WooCommerce button in editor. If so, just choose Product Price/cart option. This will make a new short code in our page like below one.

		[add_to_cart id="" sku=""]

*   Else copy paste above short code in to our page / post.

###  Step 3 – Fill the blank space

*   Just insert the ID we taken in Step 1 on this short code.

		[add_to_cart id=”218″ sku=”Prod-03″]

Sku is optional, however, id is required one.

Click save and view post / page and we can see a nice little add-to-cart button for our product on that page. When a user click on that add to cart button, then the item is automatically added to his cart without going to product page.
