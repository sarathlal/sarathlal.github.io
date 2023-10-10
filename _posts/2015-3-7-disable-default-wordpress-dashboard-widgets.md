---
title: Disable default WordPress dashboard widgets
author: 
layout: post
tags:
  - WordPress
---

When we login in to WordPress dashboard, the WordPress display few dashboard widgets. In almost WordPress installations, some of these widgets don't have any role in daily operations from the view a normal WordPress user.

So, when I deliver WordPress site for my clients, I like to hide these unnecessary widgets from there dashboard. We can simply hide them using screen options at the top of page.

But if you like to programmatically hide them from your theme, just use below codes in your theme's or child theme's `functions.php` file.

	function my_custom_dashboard_widgets() {
		global $wp_meta_boxes;
		
		//Uncomment line to hide dashboard widget
		
		//unset($wp_meta_boxes['dashboard']['normal']['core']['dashboard_activity']);
		//unset($wp_meta_boxes['dashboard']['normal']['core']['dashboard_right_now']);
		//unset($wp_meta_boxes['dashboard']['normal']['core']['dashboard_recent_comments']);
		//unset($wp_meta_boxes['dashboard']['normal']['core']['dashboard_incoming_links']);
		//unset($wp_meta_boxes['dashboard']['normal']['core']['dashboard_plugins']);
		//unset($wp_meta_boxes['dashboard']['side']['core']['dashboard_primary']);
		//unset($wp_meta_boxes['dashboard']['side']['core']['dashboard_secondary']);
		//unset($wp_meta_boxes['dashboard']['side']['core']['dashboard_quick_press']);
		//unset($wp_meta_boxes['dashboard']['side']['core']['dashboard_recent_drafts']);
		
		// bbpress
		//unset($wp_meta_boxes['dashboard']['normal']['core']['bbp-dashboard-right-now']);
		
		// yoast seo
		//unset($wp_meta_boxes['dashboard']['normal']['core']['yoast_db_widget']);
		
		// gravity forms
		//unset($wp_meta_boxes['dashboard']['normal']['core']['rg_forms_dashboard']);
		
	}
	add_action('wp_dashboard_setup', 'my_custom_dashboard_widgets', 999);
