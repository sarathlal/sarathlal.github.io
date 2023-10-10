---
title: Create MySql database and user - command line
layout: post
tags:
  - Linux
  - Server
  - MySql Server
  - Linux Commands
---

The MySql server is a commonly used database server in web applications. To manage database and content, we have too many GUI tools like `phpMyAdmin` and `adminer` etc.

But it is essential to familiarize basic commands to manage a MySql server via command line.

Login to mysql as root user.

	mysql -u root -p

it will ask for mysql root password

If you entered correct password, you should now be at a MySQL prompt that looks very similar to this:

	mysql>

Then create our database.

	CREATE DATABASE IF NOT EXISTS sample_database;

To view the database you’ve created, use the following command.

	SHOW DATABASES;

Your result should be similar to this:

mysql> SHOW DATABASES;

	+--------------------+
	| Database           |
	+--------------------+
	| information_schema |
	| mysql              |
	| test               |
	| sample_database    |
	+--------------------+
	4 rows in set (0.00 sec)

Create new user with password

	CREATE USER 'db_user'@'localhost' IDENTIFIED BY 'my_password';

Grand permission to new user on new database.

	GRANT ALL PRIVILEGES ON sample_database.* TO 'db_user'@'localhost' IDENTIFIED BY 'my_password';

Once you have finalized the permissions that you want to set up for your new users, always be sure to reload all the privileges.

	FLUSH PRIVILEGES;

