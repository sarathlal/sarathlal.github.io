---
title: Optimize Magento 1 Database by clean up log entries for better performance
author: sarathlal
layout: post
tags:
  - Magento 1
---



To track each activity in Magento powered stores, Magento keep large amount of data on its database as log entries. Tracking activities always help us to improve sales. But the large database make our site as slow & it will suck.

So today, I'm going to clean my Magento database for a well optimized Magento store.

We have two option to remove log entries from Magento database.

## Cleaning Logs via Magento Admin Panel

The Magento have built-in utility to clean up log files. But in default, it is disabled and most of us are unaware of it.

This is the easiest way for a non technical store owners who don’t want to play with the Magento store’s database.

To enable log cleaning utility, just follow below steps.

1. Log in to our Magento Admin Panel.
2. Go to System => Configuration.
3. On the left under Advanced click on System. (Advanced => System)
4. Under system, we can see “Log Cleaning” option.
5. Fill the desired “Log Cleaning” option values and click Save.

## Cleaning Logs via phpMyAdmin

If we are comfortable with database & tools like phpMyAdmin, we have one more option. We can use phpMyAdmin to empty tables that store log details.

The benefit of this method is it allow us to clean whatever we like. We can even clean tables which aren’t included in default Magento’s Log Cleaning tool.

But we want to care too much in such situations because we are going to play with our clients valuable datas. So always try to keep a copy of original database & then we can go further.

We just want to empty below tables from Magento database using  phpMyAdmin.

    dataflow_batch_export
    dataflow_batch_import
    log_customer
    log_quote
    log_summary
    log_summary_type
    log_url
    log_url_info
    log_visitor
    log_visitor_info
    log_visitor_online
    report_viewed_product_index
    report_compared_product_index
    report_event

Always remember that we are here to empty (Truncate) selected tables & not to drop them. Be very careful when we do this action.

Performing this cleaning on regular basis will definitely improve our Magento store’s performance and efficiency.
