---
title: Composer - Installation and how to use Composer in PHP project
layout: post
tags:
  - PHP
  - Composer
---

PHP Composer is a dependency manager for PHP. It allows us to declare the dependencies our project needs and installs them all automatically. This makes it easy to keep our project up-to-date, as well as share dependencies with other projects.

### Check If PHP has been Installed

    php -v

### Install Composer

    sudo curl -sS https://getcomposer.org/installer | php

### Move file to somewhere in our PATH

    mv composer.phar /usr/local/bin/composer

### General Commands to work with Composer

Check the current version of Composer:

    composer -v

Update the latest version of Composer:

    composer -selfupdate

Clear the Cache memory of Composer (to force Composer to reload libraries in the Cache memory):

    composer clearcache

Search for library packages:

    composer search library_name

## Use Composer in PHP Projects

### Create the composer.json file

This file contains all the data for setting up `Composer` for the project. To create the composer.json file, use the bellow command to the terminal.

    composer init

This command guides us to create our composer.json file. Share the proper answer & we can see the preview at the end.

Check our project folder & we can see the newly created composer.json file.

### Include Libraries into the PHP Project with Composer

#### Method 1 : using `composer require` command

    composer require vendor/package

*Example*

    composer require phpro/grumphp

This command will trigger Composer to download the `phpro/grumphp` library. The `phpro/grumphp` library will be saved in the vendor directory in our project.

Also check the `composer.json` file. The following code will be added in the file.

    "require": {
            "phpro/grumphp": "^1.6.0"
        }

#### Method 2 : Add required libraries in `composer.json` file & use `composer update` command

Edit the `composer.json` file by adding the included library into the require section.

    "library-name":"^the-smallest-version"

*Example*

    "require": {
            "phpro/grumphp": "^1.6.0",
        }

Then enter the `composer update` command to install the library. This command will automatically update the latest version of the libraries that are necessary for the PHP project.

To use the above library in our project, we have to include the `vendor/autoload.php` file in the index.php file in the PHP project.

    include vendor/autoload.php

## Remove a Library from the PHP Project

#### Method 1: Using the composer command

    composer remove vendor/package

#### Method 2: Update the composer.json file

Just go to the `composer.json` file, navigate to the require section, delete the library we want to remove and then enter the `composer update` command.
