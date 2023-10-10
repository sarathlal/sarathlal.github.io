---
title: The essential & basic WP-CLI commands for a WordPress developer
layout: post
tags:
  - WordPress
---

The `WP-CLI` is a powerful command line tool for managing WordPress. I believe that it is an essential tool for a WordPress Developer. If we know the options, it is a handy tool & we can improve our WordPress workflow.

Below you can find a large list of `WP-CLI` commands that is useful in every day.

## Install WordPress using WP-CLI

First Create `wp-config.php` file.

	wp core config --dbname=your_db_name --dbuser=your_db_user --dbpass=your_db_password --dbhost=localhost --dbprefix=wp_

*<small>I believe that you already created Database and permission for the user.</small>*

**Install WordPress**

	wp core install --url="your_domain" --title="Blog Title" --admin_user="admin_username" --admin_password="your_password" --admin_email="your_email"

## Update WordPress Core using WP-CLI

	wp core update

#### downgrade / upgrade WordPress core to a specific version

	wp core update --version=4.8.1 --force

## Plugin Management using WP-CLI
	
#### List installed plugins

	wp plugin list

#### Format the output of plugin list

There is an option to update the output format in CSV or JSON in WP-CLI.

	wp plugin list --format=json

	wp plugin list --format=csv

If you need to refine & filter the list with parameters, it is too easy.

#### List plugin names & its version only

	wp plugin list --fields=name,version

#### List inactive plugins

	wp plugin list --status=inactive

#### List update available plugins

	wp plugin list --update=available

#### Install Plugin

	wp plugin install woocommerce

#### Activate Plugin

	wp plugin activate woocommerce

#### Deactivate Plugin

	wp plugin deactivate woocommerce

## Manage theme using WP-CLI

Same like plugins, it is too easier to manage themes using WP-CLI.

#### List installed themes

	wp theme list

#### Install new theme

	wp theme install twentytwelve

#### Activate new theme

	wp theme activate twentytwelve

## Import sample data using WP-CLI

First, we have to install WordPress Import Plugin & then run the import command.

	wp import wp-content/plugins/woocommerce/dummy-data/dummy-data.xml --authors=create

## Update WordPress Options Using WP-CLI

#### Update blog name

	wp option update blogname "New blog name"

#### Update blog description

	wp option update blogdescription "New blog description"

#### Update admin email

	wp option update admin_email someone@example.com
	
#### Update time zone

	wp option update timezone_string "America/New_York"
	
#### Update `Discourage search engines from indexing this site` option
	
	wp option set blog_public 0

## Post Management using WP-CLI

#### List posts

	wp post list

#### List pages

	wp post list --post_type=page

#### Create a new post

	wp post create --post_type=post --post_title='A sample post'

#### Update an existing post status

	wp post update 123 --post_status=draft

#### Delete an existing post

	wp post delete 123

#### Launch system editor to edit post

	wp post edit 123

#### Generate multiple posts

	wp post generate --count=5

#### Generate multiple pages 

	wp post generate --post_type=page --count=3

## Migrate WordPress database using WP-CLI

When we move WordPress from one domain to another domain, we have to migrate WordPress Database. We can use WP-CLI's `search-replace` command for database migration. It is better to run this command on the new host after database is imported.

#### Migrate & View report

	wp search-replace example.com newexample.com --dry-run

#### If there is no error, migrate & save DB.

	wp search-replace example.com newexample.com
	
## Database backup using WP-CLI

	wp db export

A backup of our database in a `.SQL` format will be available at the root of our website.

The options are never end. To know more about WP-CLI, I suggest to check the [WordPress Codex page](https://developer.wordpress.org/cli/commands/){:target="_blank"}.
