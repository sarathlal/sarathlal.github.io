---
title: Create shipping zone and add shippig method in to shipping zone using WP-CLI - WooCommerce
layout: post
tags:
  - WordPress
  - WP-CLI
---

For a DevOps project, I need to to create shipping zone and add shippig method in to shipping zone in WooCommerce using WP-CLI. Here is the quick commands to achive the requirement.

## List shiping zone

	wp wc shipping_zone list --user=<user_name>

## Create new shipping zone

	wp wc shipping_zone create --name=<zone_name> --user=<user_name>
	
**example**

	wp wc shipping_zone create --name="sample" --user=admin

I need to get newly created zone ID. So I have added `--porcelain` argument with command.

	wp wc shipping_zone create --name="sample" --porcelain --user=admin

## List available shipping method in a shipping zone

	wp wc shipping_zone_method list <zone_id> --user=<user_name>

**Example**

	wp wc shipping_zone_method list 1 --user=admin

## Add shipping methods in newly created shipping zone

	wp wc shipping_zone_method create <zone_id> --method_id=<method_id> --user=<user_name>

**Example**

	wp wc shipping_zone_method create 1 --method_id="flat_rate" --user=admin

	wp wc shipping_zone_method create 1 --method_id="free_shipping" --user=admin

	wp wc shipping_zone_method create 1 --method_id="local_pickup" --user=admin

There are few more interesting WC related commands are available. Check the below link for details.

[https://github.com/woocommerce/woocommerce/wiki/WC-CLI-Commands](https://github.com/woocommerce/woocommerce/wiki/WC-CLI-Commands)
