---
title: Get WordPress SQL query details
layout: post
tags:
  - WordPress
---

When I debug WordPress, getting SQL query details is useful in some situations.

In the WordPress plugin repo, we can find some nice debug plugins to get query details. Also, we can use default WordPress options to get query details.

First, we need to add a definition in our `wp-config.php`.

	define('SAVEQUERIES', true);

The SAVEQUERIES definition saves the database queries to an array and we can use that array to analyze those queries.

The array is stored in the global `$wpdb->queries`.

### Print last SQL query string

	$wpdb->last_query

### Print last SQL query result

	$wpdb->last_result

### Print last SQL query Error

	$wpdb->last_error
