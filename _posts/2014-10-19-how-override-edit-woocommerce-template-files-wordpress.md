---
title: 'How Override / edit WooCommerce template files &#8211; WordPress'
author: sarathlal
layout: post
tags:
  - WooCommerce
  - WordPress
---
The WooCommerce plugin have its own template files and Markup. In some WordPress + WooComerce customization, we want to edit WooCommerce template files.

The safest and recommend way to edit WooComerce template file is via overriding them from our theme.

The whole WooCommerce template files located within the `/woocommerce/templates/ `directory in WordPress plugin folder.

We just want to copy the files we want to edit into a directory within our theme named `/woocommerce/` with the same file structure.

For example, to override the admin order notification, copy: `woocommerce/templates/emails/admin-new-order.php` from plugin folder to `ourtheme/woocommerce/emails/admin-new-order.php.`

The copied file will now override the WooCommerce default template file.
