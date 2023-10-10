---
title: Conditional tags for order thank you page - WooCommerce
layout: post
tags:
  - WooCommerce
tested: WordPress 5.2, WooCommerce 3.6.5
---

In WooCommerce, if you need to check that current page is an order thank you page, you can  use below conditional tags in your code.

1. `is_order_received_page()`
2. `is_wc_endpoint_url( 'order-received' )`

