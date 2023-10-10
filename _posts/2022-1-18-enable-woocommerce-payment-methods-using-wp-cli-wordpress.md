---
title: Enable WooCommerce payment methods using WP-CLI
layout: post
tags:
  - WordPress
  - WP-CLI
---

Today, I need to enable WooCommerce payment methods using WP-CLI. Here is the quick command.

	wp wc payment_gateway update <id> --user=<user_name>

To enable payment gateway, we need payment gateway ID. To get the payment gateway ID, we can use `payment_gateway list` command.

    wp wc payment_gateway list --user=<user_name>

**Example**

	wp wc payment_gateway update bacs --enabled=1 --user=<user_name>
	wp wc payment_gateway update cheque --enabled=1 --user=<user_name>
	wp wc payment_gateway update cod --enabled=1 --user=<user_name>

[https://github.com/woocommerce/woocommerce/wiki/WC-CLI-Commands](https://github.com/woocommerce/woocommerce/wiki/WC-CLI-Commands)
