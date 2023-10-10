---
title: Action hooks that trigger on, before or after add, update or delete actions of option - WordPress
layout: post
tags:
  - WordPress
tested: WordPress 5.2
---

If we need to debug add, update or delete actions on the `wp_options` table, we can use below hooks.

### add_option

Fires before an option is added.

	add_action('add_option', function( $option_name, $option_value ) {
		//....
	}, 10, 2);

### add_option_{$option}

Fires after a specific option has been added.

	add_action('add_option_foo', function( $option_name, $option_value ) {
		 //....
	}, 10, 2);

### added_option

Fires after an option has been added.

	add_action('added_option', function( $option_name, $option_value ) {
			 //....
	}, 10, 2);

### update_option

Fires immediately before an option value is updated.

	add_action('update_option', function( $option_name, $old_value, $new_value ) {
		//....
	}, 10, 3);

### update_option_{$option}

FFires after the value of a specific option has been successfully updated.

	add_action('update_option_foo', function( $option_name, $old_value, $new_value ) {
		 //....
	}, 10, 3);

### updateed_option

Fires after an option has been successfully updated.

	add_action('updated_option', function( $option_name, $old_value, $new_value ) {
			 //....
	}, 10, 3);

### delete_option

Fires immediately before an option is deleted.

	add_action('delete_option', function( $option_name ) {
			 //....
	}, 10);

### delete_option{$option}

Fires after a specific option has been deleted.

	add_action('delete_option_foo', function( $option_name ) {
		 //....
	}, 10);

### deleted_option

Fires after an option has been deleted.

	add_action('deleted_option', function( $option_name ) {
			 //....
	}, 10);

