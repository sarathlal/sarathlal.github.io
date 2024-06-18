---
layout: post
title:  How to Hide WooCommerce Gallery Images from Non-Logged-In Users
meta-description: Learn how to hide WooCommerce gallery images from non-logged-in users on the single product page with this simple code snippet. Enhance your store's privacy and exclusivity.
tags:
  - WordPress
  - WooCommerce
---

In this guide, I will show you how to hide gallery images on single product pages from non-logged-in users in WooCommerce. This can be useful for offering exclusive content to registered users or members, and it enhances privacy for sensitive product images.


#### Code Implementation

Add the following code snippet to your child theme's `functions.php` file:

```php
function hide_product_gallery_for_non_logged_in_users() {
    if ( ! is_user_logged_in() ) {
        remove_action( 'woocommerce_product_thumbnails', 'woocommerce_show_product_thumbnails', 20 );
    }
}
add_action( 'wp', 'hide_product_gallery_for_non_logged_in_users' );
```

#### How it works

1. **Check if the User is Logged In**: The `is_user_logged_in()` function checks whether the current user is logged in. If the user is not logged in, the code proceeds to remove the gallery images.
2. **Remove the Gallery Images**: The `remove_action` function removes the `woocommerce_show_product_thumbnails` action from the `woocommerce_product_thumbnails` hook, hiding the gallery images on the single product page.

### Testing the Implementation

After adding the code, you should test it to ensure it works as expected:

1. **Log Out**: Log out from WordPress account.
2. **Visit a Product Page**: Navigate to a single product page on the site. You should notice that the gallery images are not displayed.
3. **Log In**: Log back into the WordPress account.
4. **Visit the Product Page Again**: The gallery images should now be visible.

Hiding WooCommerce gallery images from non-logged-in users is a straightforward customization that can enhance our store’s privacy and exclusivity. By adding a simple function, we can control the visibility of our product images effectively.

