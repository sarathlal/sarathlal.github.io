---
title:  Install WP-CLI
layout: post
tags:
  - WordPress
---

### Prerequisite

1. UNIX-like environment (OS X, Linux, FreeBSD, Cygwin)
2. PHP 5.6 or later
3. WordPress 3.7 or later.

Download `wp-cli.phar`.

    sudo curl -O https://raw.githubusercontent.com/wp-cli/builds/gh-pages/phar/wp-cli.phar

To use WP-CLI from the command line by typing `wp`, make the file executable and move it to somewhere in our PATH.

    chmod +x wp-cli.phar
    sudo mv wp-cli.phar /usr/local/bin/wp

We can confirm that WP-CLI was installed correctly with below command.

    wp --info

[https://wp-cli.org/](wp-cli.org)
