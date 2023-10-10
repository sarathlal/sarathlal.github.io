---
title:  Install theme unit test data using WP-CLI - WordPress
layout: post
tags:
  - WordPress
---

The theme unit testing is an essential act in WordPress theme development. When we make a new WordPress theme or starting a new WordPress project, it must be our first task after the WordPress installation.

It is too simple.

1. Download theme test data
2. Add & activate WordPress Import Plugin
3. Import the test data.

Below you can find the `WP-CLI` commands for all of the above tasks.

	curl -O https://wpcom-themes.svn.automattic.com/demo/theme-unit-test-data.xml
	wp plugin install wordpress-importer --activate
	wp import ./theme-unit-test-data.xml --authors=create
	rm theme-unit-test-data.xml
