---
title: Add / change default user password in PostgreSQL
layout: post
tags:
  - PostgreSQL
---

In most Unix distributions, the default Postgres user neither requires nor uses a password for authentication. But if you like to set a password for the user, you can follow the below steps.

## Login to CLI as the default user

	sudo -u postgres psql

## Change password

	ALTER USER postgres PASSWORD 'myPassword';
