---
title:  Install Magento 2 using composer
layout: post
tags:
  - Magento 2
---

The Magento 2 can be installed in multiple ways. I like the composer way & below you can find the steps to install Magento 2 using composer.

### Prerequisites

1. LAMP Server
2. Composer
3. Server access via SSH
4. Valid Magento Authentication keys ([Create authentication keys](http://devdocs.magento.com/guides/v2.0/install-gde/prereq/connect-auth.html){:target="_blank"})

During installation, our command line interface will ask for Magento authentication keys. The public key is our user name & private key is password.

## Create new project

	composer create-project --repository-url=https://repo.magento.com/ magento/project-community-edition web/mag2.local.me/public_html

You have to update your installation directory in the above command. Mine it is `web/mag2.local.me/public_html` for my URL `http://mag2.local.me`.

## Install Magento

	php bin/magento setup:install 
	--base-url="http://mag2.local.me/" 
	--db-host="localhost" 
	--db-name="my_dbname" 
	--db-user="my_dbuser" 
	--db-password="dbpassword" 
	--admin-firstname="admin" 
	--admin-lastname="admin" 
	--admin-email="admin@domain.com" 
	--admin-user="admin_username" 
	--admin-password="admin_password" 
	--language="en_US" 
	--currency="USD" 
	--timezone="America/Chicago" 
	--use-rewrites="1" 
	--backend-frontname="my-admin-path"

I have added new lines in the installation command for better readability. Update the values in the installation command and remove the new lines.

It will look like below one.

	php bin/magento setup:install --base-url="http://mag2.local.me/" --db-host="localhost" --db-name="my_dbname" --db-user="my_dbuser" --db-password="dbpassword" --admin-firstname="admin" --admin-lastname="admin" --admin-email="admin@domain.com" --admin-user="admin_username" --admin-password="admin_password" --language="en_US" --currency="USD" --timezone="America/Chicago" --use-rewrites="1" --backend-frontname="my-admin-path"

Magento 2 will be installed and you can see message in your interface. You can confirm that by accessing its front end & back end.

## Add sample data

The current installation is without sample data. If required, we can easily install sample data.

#### Go to project root folder

	cd web/mag2.local.me/public_html

#### Update our `composer.json` file & install sample data

	php bin/magento sampledata:deploy
	php bin/magento setup:upgrade

## Compile installation after new changes

	php bin/magento setup:di:compile
