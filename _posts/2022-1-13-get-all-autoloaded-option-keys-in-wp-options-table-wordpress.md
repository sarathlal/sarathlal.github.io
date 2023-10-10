---
title: Get all autoloaded option keys in wp_options table - WordPress
layout: post
tags:
  - WordPress
---

We can use functions like `add_option()` and `update_option()` to create options in the `wp_options` table.

As you noticed, the 4th parameter for `add_option()` & 3rd parameter for `update_option()` function are `autoload` & the default value is `yes`.

>"Whenever a request comes to WordPress, it has to make many complicated and quick decisions in order to serve the right information to a user. One well-known way to improve the speed at which this can be done is to define certain options as needed on every page load and others as not really that important.  The way you do this is  by setting an option to autoload = yes.  When you do that, WordPress will store all of those options into a single object and load them on every page load."

The above statement is copied from [WP VIP reference](https://docs.wpvip.com/technical-references/code-quality-and-best-practices/working-with-wp_options/) regarding options table.

I believe that you can understand the issue now. If we set our option value to autoload, it is a major performance issue. To resolve this issue, first we need to identify the autoloaded option keys in `wp_options` table.

Here is the quick `SQL` query to get all option key & data size. If your table prefix is not `wp`, you need to modify `SQL` as per your table prefix.

    SELECT 'autoloaded data in KiB' as name, ROUND(SUM(LENGTH(option_value))/ 1024) as value FROM wp_options WHERE autoload='yes'
    UNION
    SELECT 'autoloaded data count', count(*) FROM wp_options WHERE autoload='yes'
    UNION
    (SELECT option_name, length(option_value) FROM wp_options WHERE autoload='yes' ORDER BY length(option_value) DESC LIMIT 100)

