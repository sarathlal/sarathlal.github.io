---
title: Create and use custom Image attribute in Magento 1
author: sarathlal
layout: post
tags:
  - Magento 1
---

When customizing Magento stores, often our clients have a demand that they need some additional image attributes for each products like banner image etc.

In my latest Magento customization, our client requested such an additional image attribute for each product. The Magento already have option to add as much as new attributes for our products.

We just want to effectively use this built-in feature. So today, I'm trying to briefly explain different steps to add a fourth Image attribute in Magento store.

## Create a new image attribute

1. Hover on `Catalog`, then `Attributes`, then click `Manage Attributes` from Magento main menu on back end.
2. Click “Add New Attribute”.
3. Give an attribute code to our new attribute.
4. Set the store level we are using it (or Global if we want it everywhere).
5. Then under `Catalog Input Type for Store Owner` choose `Media Image`.
6. If we will use it on all our product types, keep `All Product Types`. Else choose the product type you wish.
7. On the second tab (Manage Label/Options), give the image position a name that will appear in various places, such as the admin & different store views.
8. Then click “Save Attribute” to save the attribute.

To use this new image attribute on our Magento store, we want to add this new attribute in to an attribute set. 

1. Hover on `Catalog`, then `Attributes`, then click `Manage Attribute Sets`.
2. Click on the attribute set we wish to add the new image attribute.
3. Drag the new attribute we created from the right over to the `Images` folder in the center.
4. Then click “Save Attribute Set” on the right side.

From now, we can see a fourth image option in Magento product image section. Now we can upload images and then select this new image attribute for uploaded images.

## Display custom Image attribute in Magento front end

If we selected uploaded images as this new attribute in back-end, they also become available in Magento product collection on front end. But we want to use Magento Catalog Image helper to get full URL of this Image.
		
Inside Product view (template/catalog/product/view.phtml), just use below code to retirve new image attribute.

		$hdr_img = $cur_product->getResource()->getAttribute('header_img');
		if ($hdr_img)
		{
			$ban_img = $this->helper('catalog/image')->init($cur_product, 'header_img')->resize(1600, 312);
			echo $ban_img;
		}
		
## Solve errors due to absence of place holder image

Few days ago, I was successfully set upped a new image attribute for product in a Magento store and noticed that Magento generate unexpected error on front view in absence of value in new image attribute.

Magento have some place holder images for its default image attributes. If we miss images for this default image attribute (small image, base image, thumbnail etc), Magento display this place holder images instead of product images.

Now I created a new custom image attribute for Magento store. But I forget to add place holder image for this new attribute. So Magento generate error that says there was an image missing.

We have option to upload placeholder image from back-end in Magento. Just go to System -> Configuration -> Catalog -> Product Image Placeholders. Then upload images for all the types.

Also we can manually insert placeholder image for new custom attribute.

We want to insert an image in our skin like `skin/frontend/{interface}/{theme}/images/catalog/product/placeholder/rollover_image.jpg` to use a the default image for the `rollover_image` attribute. That is enough.
