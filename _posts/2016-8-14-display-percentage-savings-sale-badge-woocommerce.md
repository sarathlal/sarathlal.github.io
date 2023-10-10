---
title: Display percentage of savings on sale badge - WooCommerce
layout: post
tags:
  - WordPress
  - WooCommerce
---

In WooCommerce, if an item have a sale price (special price), there will be a savings for your customer. In default, WooCommerce display a sale badge on such instance.

Instead of displaying this plain sale badge, we can display the percentage of saving on this sale badge  & it will help to increase the sales.

	add_filter('woocommerce_sale_flash', 'tr245_woo_savings_on_sales_flash');

	function tr245_woo_savings_on_sales_flash()
	{
	global $post, $product;
		if ( ! $product->is_in_stock() ) return;
		$sale_price = get_post_meta( $product->id, '_price', true);
		$regular_price = get_post_meta( $product->id, '_regular_price', true);
		if (empty($regular_price)){ //then this is a variable product
			$available_variations = $product->get_available_variations();
			$variation_id=$available_variations[0]['variation_id'];
			$variation= new WC_Product_Variation( $variation_id );
			$regular_price = $variation ->regular_price;
			$sale_price = $variation ->sale_price;
		}
		$savings = ceil(( ($regular_price - $sale_price) / $regular_price ) * 100);
		$sale_flash = '<span class="onsale"> - ' . $savings . '%</span>';
		return $sale_flash;
	}
