---
title: Install PostgreSQL 11 on Debian 10 (Buster)
layout: post
tags:
  - PostgreSQL
  - Debian 10
---

## Setup PostgreSQL PPA

First, import PostgreSQL packages signing key on our system.

	wget -q https://www.postgresql.org/media/keys/ACCC4CF8.asc -O - | sudo apt-key add -

Now add PostgreSQL apt repository.

	sudo sh -c 'echo "deb http://apt.postgresql.org/pub/repos/apt/ buster-pgdg main" >> /etc/apt/sources.list.d/pgdg.list'

## Install PostgreSQL

Update the repository list & install PostgreSQL.

	sudo apt-get update
	sudo apt-get install postgresql postgresql-contrib

## Turn on PostgreSQL server

	sudo systemctl start postgresql

## Login to PostgreSQL CLI as user postgres

After installing the PostgreSQL database server by default, it creates a user ‘postgres’ with the role ‘postgres’. It also creates a system account with the same name ‘postgres’. 

So now login to our system as user postgres and connect the database.

	sudo -u postgres psql

To exit from PostgreSQL database CLI interface, use the below command.

	\q
