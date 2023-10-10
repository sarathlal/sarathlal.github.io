---
title: Customized Product Query using WP_Query - WooCommerce
layout: post
tags:
  - WordPress
  - WooCommerce
---

The WordPress have a nice class - `WP_Query` & I'm regularly using that one to make customized query on my post entries. The entries may be posts, pages or custom post type entries.

In one of my recent WooCommerce project, I have to fetch & display products as per specific parameters. The WooCommerce have some nice option to fetch & filter the products. But our client requirement is extremely higher than this default options. 

So to get extreme filtering, I have used `WP_Query` and it make some sense.

Below I have added few sample code to fetch products with `WP_Query`. I believe that it is a good reference for my upcoming projects.

	$params = array(
		'posts_per_page' => 5, //No of product to be fetched
		'post_type' => 'product'
	);
	
	$wc_query = new WP_Query($params);
	if ($wc_query->have_posts()) :
		while ($wc_query->have_posts()) :
			$wc_query->the_post();
			?>
			<?php the_title(); ?>
	<?php
		endwhile;
			wp_reset_postdata();
	else:  ?>
		<p><?php _e( 'No Products' );?></p>	
	<?php endif;

We have to update our query parameter as per the conditions.

### Display products in a specific product types only

The product type in WooCommerce is a custom taxonomy, so we have to add taxonomy parameters in our query.

	$params = array(
		'posts_per_page' => 5,
		'post_type' => 'product',
		'tax_query' => array(
			array(
				'taxonomy' => 'product_type',
				'field'    => 'slug',
				'terms'    => 'our_type', 
			),
		),
	);

If you plan to use your own custom product types in WooCommerce, the `terms` argument is the same as in the `$this->product_type = 'our_type'` part of our new product type's class constructor.

### Display products with sale price

	$params = array(
		'posts_per_page' => 5,
		'post_type' => 'product',
		'meta_key' => '_sale_price',
		'meta_value' => '0',
		'meta_compare' => '>='
	);

### Display products that have a sale price for product variation

	$params = array(
		'posts_per_page' => 5,
		'post_type' => array('product', 'product_variation'),
		'meta_key' => '_sale_price',
		'meta_value' => 0,
		'meta_compare' => '>='
		'meta_type' => 'NUMERIC'
	);

### Display products that have a price below a value

The below example display products thats price below than 5.

	$params = array(
		'posts_per_page' => 5,
		'post_type' => array('product', 'product_variation'),
		'meta_query' => array(
			'relation' => 'OR',
			array(
				'key' => '_price',
				'value' => 5,
				'compare' => '<=',
				'type' => 'NUMERIC'
			),
			array(
				'key' => '_sales_price',
				'value' => 5,
				'compare' => '<=',
				'type' => 'NUMERIC'
			)
		)
	);

### Display products in a given price range

The price range will be 10 - 15 and the below code will display few products in this price range.

	$params = array(
        'posts_per_page' => 5,
        'post_type' => array('product', 'product_variation'),
        'meta_query' => array(
            'relation' => 'OR',
            array(
                array(
                    'key' => '_price',
                    'value' => 10,
                    'compare' => '>=',
                    'type' => 'NUMERIC'
                ),
                array(
                    'key' => '_price',
                    'value' => 15,
                    'compare' => '<=',
                    'type' => 'NUMERIC'
                )
            ),
            array(
                array(
                    'key' => '_sale_price',
                    'value' => 10,
                    'compare' => '>=',
                    'type' => 'NUMERIC'
                ),
                array(
                    'key' => '_sale_price',
                    'value' => 15,
                    'compare' => '<=',
                    'type' => 'NUMERIC'
                )
            )
        )
	);

### Display products as per the stock status

The below code display products that have stock value as In Stock.

	$params = array(
        'posts_per_page' => 5,
        'post_type' => array('product', 'product_variation'),
        'meta_query' => array(
            array(
                'key' => '_stock_status',
                'value' => 'instock'
            )
        )
	);

### Display products with a defined stock level

The below code display products that have more than 5 as stock.

	$params = array(
        'posts_per_page' => 5,
        'post_type' => array('product', 'product_variation'),
        'meta_query' => array(
            array(
                'key' => '_stock',
                'value' => 5,
                'compare' => '>',
                'type' => 'NUMERIC'
            )
        )
	);

