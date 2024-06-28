---
layout: post
title:  Dynamically Apply a Coupon in Easy Digital Downloads After Adding an Item to the Cart
meta-description: Learn how to automatically apply coupon codes in Easy Digital Downloads after adding specific items to the cart. Boost your sales and improve customer satisfaction with this simple code snippet.
tags:
  - WordPress
  - Easy Digital Download
  - EDD
---

In the competitive world of e-commerce, offering dynamic discounts can significantly enhance the user experience and increase sales. Easy Digital Downloads (EDD) is a popular WordPress plugin for selling digital products, and it offers robust features for managing discounts and promotions. In this blog post, we will explore a practical way to automatically apply a coupon code when a user adds a specific item to their cart. This approach can be particularly useful for promoting selected products or offering exclusive deals.

### The Requirement

Our goal is to apply a specific coupon code automatically after a user adds certain products to their cart. This means that if a user adds any of the designated items to their cart, the coupon code will be applied without any manual input from the user. This seamless experience can lead to higher conversion rates and improved customer satisfaction.

### The Code Snippet

To achieve this functionality, we will use a hook provided by Easy Digital Downloads. The following code snippet demonstrates how to dynamically apply a coupon after a product is added to the cart:

```php
// Hook into the action after adding to cart
add_action('edd_post_add_to_cart', 'th36t_apply_coupon_after_adding_to_cart');
function th36t_apply_coupon_after_adding_to_cart($download_id) {

    $discounted_download_ids = array(12, 20, 17);

    if(in_array($download_id, $discounted_download_ids)){
        // Define coupon code
        $coupon_code = 'PRIVILEGE50';

        // Check if the coupon is valid
        $coupon_id = edd_get_discount_id_by_code($coupon_code);
        if ($coupon_id && edd_is_discount_active($coupon_id)) {
            // Check if the discount is already applied to prevent duplicates
            $cart_discounts = edd_get_cart_discounts();
            if (!in_array($coupon_code, $cart_discounts)) {
                // Apply the coupon to the cart
                edd_set_cart_discount($coupon_code);
            }
        }
    }
}
```

### Explanation of the Code

**Hook into the Action**:

```
add_action('edd_post_add_to_cart', 'th36t_apply_coupon_after_adding_to_cart');
```

This line hooks our custom function into the `edd_post_add_to_cart` action, which is triggered after a product is added to the cart.

**Define the Function**:

```php
function th36t_apply_coupon_after_adding_to_cart($download_id) {
```
   This function is defined to execute our logic for applying the coupon.

**Specify Discounted Products**:
```php
$discounted_download_ids = array(12, 20, 17);
```
   Here, we list the product IDs that are eligible for the discount. If the added product matches one of these IDs, the coupon will be applied.

**Check and Apply the Coupon**:
```php
if(in_array($download_id, $discounted_download_ids)){
// Define coupon code
$coupon_code = 'PRIVILEGE50';

// Check if the coupon is valid
$coupon_id = edd_get_discount_id_by_code($coupon_code);
if ($coupon_id && edd_is_discount_active($coupon_id)) {
   // Check if the discount is already applied to prevent duplicates
   $cart_discounts = edd_get_cart_discounts();
   if (!in_array($coupon_code, $cart_discounts)) {
       // Apply the coupon to the cart
       edd_set_cart_discount($coupon_code);
   }
}
}
```

This block checks if the added product ID is in our discounted products list. If it is, it verifies if the coupon is valid and active. Finally, it checks if the coupon is already applied to the cart to avoid duplicates and then applies the coupon.

### Benefits of This Approach

- **Automated Discounts**: Customers automatically receive discounts on eligible products, enhancing their shopping experience.
- **Increased Conversions**: By simplifying the discount process, customers are more likely to complete their purchases.
- **Targeted Promotions**: Easily promote specific products by dynamically applying coupons.

Implementing dynamic coupon application in Easy Digital Downloads can significantly streamline the shopping experience for your customers. By using the provided code snippet, you can ensure that discounts are applied seamlessly, boosting your sales and customer satisfaction. Feel free to customize the code to suit your specific requirements and enjoy the benefits of automated discounts.
