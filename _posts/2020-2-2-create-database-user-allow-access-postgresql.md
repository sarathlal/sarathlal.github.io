---
title: Create database, user & allow access - PostgreSQL
layout: post
tags:
  - PostgreSQL
---

### Connect to PostgreSQL server instance

    sudo -u postgres psql

### Create Database

    CREATE DATABASE database_name;

### Connect to Database

    \c database_name;

### Create User

    CREATE USER user_name WITH PASSWORD 'user_password';

### Grant privileges

    GRANT ALL PRIVILEGES ON DATABASE "database_name" to user_name;

### Delete database

    DROP DATABASE IF EXISTS database_name;

