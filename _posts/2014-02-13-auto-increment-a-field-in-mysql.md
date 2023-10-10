---
title: AUTO INCREMENT a Field in MySQL
author: sarathlal
layout: post
tags:
  - MySQL
---
Very often, we want to make columns as auto increment in Database. By specifying AUTO_INCREMENT to the primary key field, we can make column value as auto incrementing in MySQL.

The below code create a simple table &#8220;Employees&#8221; with a single auto increment column named as &#8220;ID&#8221;.

	CREATE TABLE Employees
	(
	ID int NOT NULL AUTO_INCREMENT,
	Name varchar(255) NOT NULL,
	Address varchar(255),
	City varchar(255),
	PRIMARY KEY (ID)
	);

By default, the starting value for AUTO_INCREMENT is 1, and it will increment by 1 for each new record.

If we want to start AUTO_INCREMENT column with another value, we can use the following SQL statement.

	ALTER TABLE table_name AUTO_INCREMENT= [New Number];


The AUTO INCREMENT interval value is controlled by the MySQL Server variable `auto_increment_increment` and applies globally. To change this to a number different from the default of 1, we can use the following command in MySQL.

	SET @@auto_increment_increment = [interval number];

To insert a new record into the &#8220;Employees&#8221; table, we will NOT have to specify a value for the &#8220;ID&#8221; column (a unique value will be added automatically):

	INSERT INTO Employees (Name,City)
	VALUES ('Blue','zzzzz');


The SQL statement above will insert a new record into the &#8220;Employees&#8221; table. The &#8220;ID&#8221; column would be assigned a unique value.
