---
layout: post
title:  Creating Easy Digital Download Coupons Dynamically
meta-description: Learn how to dynamically create Easy Digital Downloads (EDD) coupons with a 10-day expiry using custom PHP code. Enhance your promotional strategies with automated coupon creation on user registration.
tags:
  - WordPress
  - Easy Digital Download
  - EDD
---

Creating Easy Digital Downloads (EDD) coupons dynamically can greatly enhance your promotional efforts. Whether you are offering a discount for new subscribers or setting up a time-limited sale, being able to programmatically generate coupons provides flexibility and efficiency. In this blog post, we will walk you through setting up EDD coupons with a dynamic expiry date of 10 days from creation.

### Function to Create EDD Coupons with Dynamic Expiry

First, we need a function that creates a coupon and sets its expiry date dynamically to 10 days from the creation date. Add this function to your theme's `functions.php` file or a custom plugin.

```php
function create_edd_coupon($code, $amount, $type = 'percent', $products = array()) {
    if ( ! class_exists( 'EDD_Discount' ) ) {
        return false;
    }

    // Calculate the expiration date (10 days from now)
    $expiration_date = date( 'Y-m-d H:i:s', strtotime( '+10 days' ) );

    // Create the discount
    $discount = new EDD_Discount;

    // Set the discount properties
    $discount->name            = 'Dynamic Coupon';
    $discount->code            = $code;
    $discount->type            = $type;
    $discount->amount          = $amount;
    $discount->start_date      = date( 'Y-m-d H:i:s' );
    $discount->end_date        = $expiration_date;
    $discount->max_uses        = 1; // Adjust as needed
    $discount->uses            = 0;
    $discount->product_reqs    = $products;
    $discount->excluded_products = array();
    $discount->status          = 'active';
    $discount->use_once        = true; // Ensure coupon is used only once
    $discount->apply_once      = true; // Apply coupon only on the first purchase


    // Save the discount
    $discount_id = $discount->save();

    return $discount_id ? true : false;
}
```

### Example Usage of the Function

You can use this function to create a coupon whenever you need. For instance, you might want to generate a coupon for a specific promotional campaign.

```php
// Example usage
$coupon_code = 'SPECIAL20';
$coupon_amount = '20'; // 20% discount
$coupon_type = 'percent'; // Can be 'percent' or 'flat'
$product_ids = array(123, 456); // Array of product IDs this coupon applies to

$success = create_edd_coupon($coupon_code, $coupon_amount, $coupon_type, $product_ids);

if ($success) {
    echo 'Coupon created successfully!';
} else {
    echo 'Failed to create coupon.';
}
```

### Automated Coupon Creation on User Registration

To further enhance user experience, you might want to generate a coupon automatically when a new user registers on your site. Here’s how you can hook into the user registration process and create a welcome coupon.

```php
add_action('user_register', 'create_welcome_coupon', 10, 1);

function create_welcome_coupon($user_id) {
    $user_info = get_userdata($user_id);
    $coupon_code = 'WELCOME' . strtoupper($user_info->user_login);
    $coupon_amount = '10'; // 10% discount

    $success = create_edd_coupon($coupon_code, $coupon_amount, 'percent', array());

    if ($success) {
        // Optionally send the coupon code to the user via email
        wp_mail($user_info->user_email, 'Welcome Coupon', 'Thank you for registering! Use coupon code ' . $coupon_code . ' to get a 10% discount. The coupon expires in 10 days.');
    }
}
```

By following the steps outlined above, you can dynamically create EDD coupons and set them to expire 10 days after creation. This approach is particularly useful for running time-sensitive promotions and ensuring that discounts are used promptly. You can also automate the coupon creation process to enhance user engagement, such as offering a discount to new users upon registration.

Implementing these techniques will help you leverage the full potential of Easy Digital Downloads and improve your promotional strategies. Happy coding!

