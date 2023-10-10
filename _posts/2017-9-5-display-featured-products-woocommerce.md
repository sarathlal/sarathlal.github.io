---
title: Display featured products - WooCommerce
layout: post
tags:
  - WordPress
  - WooCommerce
---

In WooCommerce, there is an option to make a product as featured one. That means, we can simply highlight / list out our special products.

To display featured products, we have two options.

### Using Short Code

	[featured_products per_page="8" columns="4" orderby="date" order="desc"]
	
### Using WordPress Query

	$args = array(  
		'post_type' => 'product',
		'post_status' => 'publish', 
		'tax_query' => array(
			array(
				'taxonomy' => 'product_visibility',
				'field'    => 'name',
				'terms'    => 'featured',
				'operator' => 'IN'
			),
		),
		'posts_per_page' => 4,
		'orderby' => 'menu_order',
        'order' => 'ASC'  
	);  
	  
	$featured_query = new WP_Query( $args );  
		  
	if ($featured_query->have_posts()) :   
	  
		while ($featured_query->have_posts()) :   
		  
			$featured_query->the_post();  
			  
			$product = get_product( $featured_query->post->ID );  
			  
			// Output product information here
			var_dump($product);
			  
		endwhile;  
		  
	endif;  
	  
	wp_reset_query(); // Reset Our Query


