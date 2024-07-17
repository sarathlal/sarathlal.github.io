---
layout: post
title:  How to Hide Applied Coupon Codes on the Checkout Page in Easy Digital Downloads
description: Learn how to hide applied coupon codes on the checkout page in Easy Digital Downloads with a custom code snippet. Enhance user experience by keeping discounts discreet.
tags:
  - WordPress
  - Easy Digital Download
  - EDD
---

Easy Digital Downloads (EDD) is a popular WordPress plugin designed for selling digital products effortlessly. While its functionality is robust, there are always customizations you might need to tailor the user experience to your specific needs. One such requirement is hiding applied coupon codes on the checkout page, especially in scenarios where you automatically apply discounts to users. This blog post will walk you through the process of achieving this with a simple code snippet.

### Why Hide Applied Coupon Codes?

There are several reasons why you might want to hide applied coupon codes on your checkout page:

- **Marketing Strategies:** Automatically applied discounts based on user behavior or promotional campaigns should be subtle to maintain a clean interface.
- **Prevent Coupon Misuse:** Hiding the coupon code reduces the chances of users sharing the code indiscriminately.

### The Requirement

Recently, we encountered a scenario where a [discount needed to be applied automatically after adding an item to the cart](/dynamically-apply-coupon-easy-digital-downloads/). The next logical step was to hide the applied coupon from the checkout page to avoid confusion and maintain a clean look.

### The Solution

The solution involves using a filter in EDD to modify the way discounts are displayed on the checkout page. The following code snippet demonstrates how to hide the applied coupon code while still showing the discount rate:

```php
function modify_discount_message($html, $discount) {
    if($discount == 'PRIVILEGE50'){
        $html = '<span class="edd_discount"><span class="edd_discount_rate">(50.00%)</span>';
    }
    return $html;
}
add_filter('edd_get_cart_discount_html', 'modify_discount_message', 10, 2);
```

### How the Code Works

**Function Definition:**
    - `modify_discount_message($html, $discount)`: This function takes two parameters: the HTML content of the discount and the discount code itself.

**Conditional Check:**
    - The `if($discount == 'PRIVILEGE50')` condition checks if the applied discount code matches the specified code (in this case, 'PRIVILEGE50').

**HTML Modification:**
    - If the condition is met, the `$html` variable is modified to display only the discount rate without showing the coupon code.

**Filter Hook:**
    - The `add_filter('edd_get_cart_discount_html', 'modify_discount_message', 10, 2);` line adds the `modify_discount_message` function to the `edd_get_cart_discount_html` filter hook, ensuring the function is executed when EDD generates the cart discount HTML.

Hiding applied coupon codes on the checkout page in Easy Digital Downloads is a straightforward process that can significantly enhance the user experience. By using a simple filter hook, you can keep your checkout page clean and focused, while still offering the benefits of discounts to your customers.

This customization is particularly useful for automatically applied coupons, ensuring that your promotional strategies remain effective and visually appealing. Implement this solution today and take your EDD-powered store to the next level of user experience.
