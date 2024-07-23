---
layout: post
title: How to Update Product Quantity in WooCommerce Using Custom Code
description: Learn how to update product quantities in WooCommerce programmatically using custom code. Follow our step-by-step guide to manage inventory more effectively and customize your WooCommerce store.
tags:
  - WordPress
  - WooCommerce
---

Managing inventory is essential for any online store. WooCommerce, a popular e-commerce platform, allows you to update product quantities manually. However, there are times when you might need to update these quantities automatically through custom code. This guide will show you how to update product quantities in WooCommerce programmatically using simple, custom code.

### Why Update Product Quantities Programmatically?

Updating product quantities programmatically can be beneficial in several scenarios, such as:

- Automatically adjusting stock levels based on external inventory systems.
- Setting default stock quantities for certain products upon specific triggers.
- Implementing complex stock management rules that WooCommerce does not support by default.

### Using WooCommerce Hooks and Functions

WooCommerce provides hooks and functions that make it easy to interact with product data. In this tutorial, we will use the `woocommerce_thankyou` hook to update product quantities when an order is placed.

### Step-by-Step Guide

#### 1. Adding Custom Code to Your Child Theme's `functions.php`

To update product quantities programmatically, you need to add custom code to your child theme's `functions.php` file. Here is an example:

```php
// Function to update product stock quantity
function update_product_stock_quantity($product_id, $quantity) {
    // Get the product object
    $product = wc_get_product($product_id);
    
    // Check if the product exists
    if ($product) {
        // Update the stock quantity
        $product->set_stock_quantity($quantity);
        
        // Save the product to update the stock quantity in the database
        $product->save();
        
        // Optionally, you can set the stock status to 'instock' or 'outofstock'
        // $product->set_stock_status('instock');
        // $product->save();
    }
}

// Hook into WooCommerce to update product stock quantity when an order is placed
add_action('woocommerce_thankyou', 'custom_update_product_stock_on_order');

function custom_update_product_stock_on_order($order_id) {
    // Get the order object
    $order = wc_get_order($order_id);
    
    // Loop through the order items
    foreach ($order->get_items() as $item_id => $item) {
        // Get the product ID from the order item
        $product_id = $item->get_product_id();
        
        // Set the new quantity (example: setting it to 100)
        $new_quantity = 100;
        
        // Update the product stock quantity
        update_product_stock_quantity($product_id, $new_quantity);
    }
}
```

#### 2. Explanation of the Code

- **`update_product_stock_quantity($product_id, $quantity)` Function:** This function takes two parameters: the product ID and the new quantity. It retrieves the product object using `wc_get_product`, updates the stock quantity, and saves the changes.

- **`woocommerce_thankyou` Hook:** The `custom_update_product_stock_on_order` function is hooked to the `woocommerce_thankyou` action, which runs after an order is placed. It loops through the items in the order and updates the stock quantity for each product.

#### 3. Customization

- **Product ID and Quantity:** Customize the product ID and the new quantity according to your needs. In this example, the product quantity is set to `100` for each product in the order.

- **Stock Status:** Optionally update the stock status using `$product->set_stock_status('instock')` or `$product->set_stock_status('outofstock')`.

