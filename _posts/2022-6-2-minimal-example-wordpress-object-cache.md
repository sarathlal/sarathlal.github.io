---
title: A minimal example about WordPress object cache
layout: post
tags:
  - WordPress
  - Optimization
---

Today, I need to do the same database query (WP Query) multiple times within a single page rendering. To reduce server overload, I tried to store the first query result into WordPress default object cache & then the upcoming fetches are performed from the cache.

    function wp_object_cache_sample_function() {
        $key = "your_cache_key";
        if ( ! $query = wp_cache_get($key) ) {
            $args = array(  
                'post_type' => 'services',
                'post_status' => 'publish',
                'posts_per_page' => 8, 
                'orderby’ => 'title', 
                'order’ => 'ASC', 
            );

            $query = new WP_Query($args);
            wp_cache_set($key,$query,'',3600);
        }
        return $query;
    }


