---
title: Querying WordPress Multisite Sites With Meta Queries
layout: post
tags:
  - WordPress
  - Optimization
---

The requirement is very simple. I need to query sites in Multisite by custom site meta value.

After creating sub site, I have added custom site meta to each site with `update_site_meta`.

    update_site_meta($site_id, 'country', 'canada');

The `WP_Site_Query` was introduced to allow a faster way to query sites in a WordPress Multisite setup.

    // WP_Site_Query arguments
    $args = array(
        'meta_query' => array(
            array(
                'key'   => 'country',
                'value' => 'australia'
            )
        )
    );

    // The Site Query
    $site_query = new WP_Site_Query( $args );

