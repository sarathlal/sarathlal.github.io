---
title: Get downloadable files of a downloadable product - WooCoomerce
layout: post
tags:
  - WordPress
  - WooCommerce
---

Today, I need to get all downloadable files of a WooCommerce downloadable product in my custom function. Below, you can find the code snippet that I have used for this purpose. We need to pass the `product` object to function & that function will return the `files`, `name` & `id` in array format.


	function get_downloads($_product)
	{
		$downloads = array();
		if ($_product->is_downloadable()) {
			foreach ($_product->get_downloads() as $file_id => $file) {
				$downloads[] = array('id' => $file_id, 'name' => $file['name'], 'file' => $file['file']);
			}
		}
		return $downloads;
	}
