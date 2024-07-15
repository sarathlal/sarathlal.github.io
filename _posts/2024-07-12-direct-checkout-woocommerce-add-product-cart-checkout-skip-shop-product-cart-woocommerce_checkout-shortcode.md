---
layout: post
title:  Direct Checkout in WooCommerce - Add a Product to Cart from Checkout Page & Skip Shop, Product, and Cart Pages with woocommerce_checkout Shortcode
meta-description: Streamline your WooCommerce checkout process by adding a product in to cart from the checkout page. Learn how to skip the shop, product, and cart pages for a direct checkout experience.
tags:
  - WordPress
  - WooCommerce
---

Simplifying the checkout process can significantly enhance user experience and boost conversion rates. In this tutorial, we will show you how to streamline the WooCommerce checkout process by adding a product dropdown directly on the checkout page using the `woocommerce_checkout` shortcode. This allows customers to select products and checkout without navigating through the shop, product, and cart pages.

Follow these steps to add a product in to cart from the WooCommerce checkout page and skip intermediate pages:

#### Step 1: Allow Checkout Page Access with an Empty Cart

By default, WooCommerce redirects users to the cart page if they access the checkout page with an empty cart. To prevent this redirection, add the following filters:

```php
// Prevent redirecting to the cart page if the cart is empty
add_filter( 'woocommerce_checkout_redirect_empty_cart', '__return_false' );
add_filter( 'woocommerce_checkout_update_order_review_expired', '__return_false' );
```

This ensures users can access the checkout page even if the cart is empty.

#### Step 2: Create a Dummy Product

Create a dummy product with a zero price and make it a virtual product. Note down its product ID (e.g., 63). This dummy product will be added to the cart to ensure the checkout form is displayed.

#### Step 3: Automatically Add Dummy Product to Cart on Checkout Page Access

Ensure the cart is populated with the dummy product when accessing the checkout page:

```php
// Ensure the cart is populated on the checkout page
add_action( 'template_redirect', 'ensure_cart_has_product' );

function ensure_cart_has_product() {
    if ( is_checkout() && ! is_order_received_page() && WC()->cart->is_empty() ) {
        $default_product_id = 63; // Replace with your default product ID
        WC()->cart->add_to_cart( $default_product_id );
        wp_safe_redirect( wc_get_checkout_url() );
        exit;
    }
}
```

This code guarantees the checkout form is displayed by adding the dummy product to the cart if it's empty.

#### Step 4: Hide Dummy Product Details from Checkout Page

To hide the dummy product details from the checkout page, add a custom class and use CSS:

```php
// Add custom class to the default product in the cart
add_filter( 'woocommerce_cart_item_class', 'add_custom_class_to_default_product', 10, 3 );

function add_custom_class_to_default_product( $class, $cart_item, $cart_item_key ) {
    $default_product_id = 63; // Replace with your default product ID
    if ( $cart_item['product_id'] == $default_product_id ) {
        $class .= ' default-product';
    }
    return $class;
}

// Add custom CSS to hide the default product on the checkout page
add_action( 'wp_head', 'add_custom_css_to_checkout_page' );

function add_custom_css_to_checkout_page() {
    if ( is_checkout() ) {
        ?>
        <style>
            .default-product {
                display: none;
            }
        </style>
        <?php
    }
}
```

This code hides the dummy product from the order review section on the checkout page.

#### Step 5: Display the Product Dropdown on the Checkout Page

Add a product dropdown to the checkout page for users to select a product:

```php
// Add product dropdown to the checkout page
add_action( 'woocommerce_before_checkout_form', 'add_product_dropdown_to_checkout' );

function add_product_dropdown_to_checkout() {
    // Get all published products
    $args = array(
        'post_type'   => 'product',
        'post_status' => 'publish',
        'posts_per_page' => -1,
    );
    $products = get_posts( $args );

    echo '<div id="product-dropdown">';
    echo '<label for="product-select">Select Product:</label>';
    echo '<select id="product-select" name="product-select">';
    echo '<option value="">Select a product</option>';

    foreach ( $products as $product ) {
        $product_obj = wc_get_product( $product->ID );
        echo '<option value="' . esc_attr( $product->ID ) . '">' . esc_html( $product_obj->get_name() ) . '</option>';
    }

    echo '</select>';
    echo '</div>';
}
```

This code creates a dropdown on the checkout page, allowing users to select a product.

#### Step 6: Handle Product Selection and Add to Cart

Use JavaScript to handle the dropdown selection and add the selected product to the cart via AJAX:

```php
add_action( 'wp_footer', 'custom_js_ajax_add_to_cart' );

function custom_js_ajax_add_to_cart() {
    if ( is_checkout() ) {
        ?>
        <script type="text/javascript">
            jQuery(document).ready(function($) {
                // Handle dropdown change event
                $('#product-select').change(function() {
                    var productId = $(this).val();
                    if (productId) {
                        // Make AJAX request to add product to cart
                        $.ajax({
                            url: wc_add_to_cart_params.ajax_url,
                            type: 'POST',
                            data: {
                                action: 'add_product_to_cart',
                                product_id: productId
                            },
                            success: function(response) {
                                if (response.error && response.product_url) {
                                    window.location = response.product_url;
                                    return;
                                }
                                // Trigger cart update
                                $(document.body).trigger('wc_update_cart');
                            }
                        });
                    }
                });

                // Update order review on checkout update
                $(document.body).on('wc_update_cart', function() {
                    $.ajax({
                        url: wc_checkout_params.wc_ajax_url.toString().replace('%%endpoint%%', 'update_order_review'),
                        type: 'POST',
                        data: {
                            security: wc_checkout_params.update_order_review_nonce,
                            payment_method: $('input[name="payment_method"]:checked').val()
                        },
                        success: function(response) {
                            if (response && response.fragments) {
                                $.each(response.fragments, function(key, value) {
                                    $(key).replaceWith(value);
                                });
                                $(document.body).trigger('updated_checkout');
                            }
                        }
                    });
                });
            });
        </script>
        <?php
    }
}

// Handle AJAX request to add product to cart
add_action( 'wp_ajax_add_product_to_cart', 'add_product_to_cart' );
add_action( 'wp_ajax_nopriv_add_product_to_cart', 'add_product_to_cart' );

function add_product_to_cart() {
    $product_id = intval( $_POST['product_id'] );
    $quantity = 1; // You can customize the quantity as needed

    if ( WC()->cart->add_to_cart( $product_id, $quantity ) ) {
        wp_send_json( array(
            'success' => true,
        ) );
    } else {
        wp_send_json( array(
            'error' => true,
            'product_url' => get_permalink( $product_id ),
        ) );
    }
}
```

This JavaScript handles the dropdown change event, sends an AJAX request to add the selected product to the cart, and updates the order review section dynamically.

#### Step 7: Remove the Dummy Product from the Cart

Remove the dummy product from the cart when another product is added:

```php
// Remove default product if another product is added to the cart
add_action( 'woocommerce_add_to_cart', 'remove_default_product_if_another_added', 10, 6 );

function remove_default_product_if_another_added( $cart_item_key, $product_id, $quantity, $variation_id, $variation, $cart_item_data ) {
    $default_product_id = 63; // Replace with your default product ID

    // Check if the added product is not the default product
    if ( $product_id != $default_product_id ) {
        // Loop through cart items
        foreach ( WC()->cart->get_cart() as $cart_item_key => $cart_item ) {
            // If default product is found, remove it
            if ( $cart_item['product_id'] == $default_product_id ) {
                WC()->cart->remove_cart_item( $cart_item_key );
            }
        }
    }
}
```

This code ensures that the dummy product is removed from the cart when a real product is added.

By following these steps, you can streamline the WooCommerce checkout process by adding a product dropdown directly on the checkout page using the `woocommerce_checkout` shortcode. This allows customers to select products and checkout without navigating through the shop, product, and cart pages, thereby enhancing the user experience and potentially increasing your store's conversion rates. Feel free to customize the code snippets to suit your specific needs.

Happy coding!

## Draft Notes

If you are using WooCommerce checkout block, the above aproach never works. I'm still working on that solution.

Just compleetd hiding default product from WooCommerce checkout page with block.

```php
// Add data-product-id attribute to order summary items to identify default product
add_action( 'wp_footer', 'add_custom_js_to_checkout_block' );

function add_custom_js_to_checkout_block() {
    if ( is_checkout() ) {
        ?>
        <script type="text/javascript">
            jQuery(document).ready(function($) {
                var defaultProductId = 63; // Replace with your default product ID

                // Function to add data attributes to the order summary items
                function addDataAttributesToOrderSummaryItems() {
                    $('.wc-block-components-order-summary-item').each(function() {
                        var productName = $(this).find('.wc-block-components-product-name').text();

                        // Assuming you have a way to map product names to IDs, do the mapping here
                        var productId = mapProductNameToId(productName);

                        if (productId) {
                            $(this).attr('data-product-id', productId);
                        }
                    });
                }

                // Function to map product names to their IDs
                function mapProductNameToId(productName) {
                    // Define your mapping here. This is an example mapping.
                    var productMapping = {
                        'Sample 1': 63,
                        // Add more product mappings here
                    };

                    return productMapping[productName] || null;
                }

                // Function to hide the default product in the order summary
                function hideDefaultProduct() {
                    $('.wc-block-components-order-summary-item[data-product-id="' + defaultProductId + '"]').hide();
                }

                // Initial attribute addition and hiding
                addDataAttributesToOrderSummaryItems();
                hideDefaultProduct();

                // Re-check when the cart is updated
                $(document).on('wc-blocks-registry__update-cart', function() {
                    addDataAttributesToOrderSummaryItems();
                    hideDefaultProduct();
                });

                // Re-check when the panel toggle button is clicked
                $(document).on('click', '.wc-block-components-panel__button', function() {
                    addDataAttributesToOrderSummaryItems();
                    hideDefaultProduct();
                });

            });
        </script>
        <?php
    }
}
```
