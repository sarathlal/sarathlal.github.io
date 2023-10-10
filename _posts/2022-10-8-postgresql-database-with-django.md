---
title: Using PostgreSQL database with Django
layout: post
tags:
  - Python
  - Django
---
In default, Django uses SQLite database & Django automatically creates a SQLite database for our project. But today, I like to use the PostgreSQL database in my application & the required steps are given below.

## Connect to Postgres Database Server

    sudo -u postgres psql

## Creating Database

    CREATE DATABASE mydb;

## Creating User

    CREATE USER myuser WITH ENCRYPTED PASSWORD 'mypass';

## Modifying Connection Parameters for Django

    ALTER ROLE myuser SET client_encoding TO 'utf8';
    ALTER ROLE myuser SET default_transaction_isolation TO 'read committed';
    ALTER ROLE myuser SET timezone TO 'UTC';

## Granting Permission To The User

    GRANT ALL PRIVILEGES ON DATABASE mydb TO myuser;

## Exit the SQL prompt

    \q

## Update Django configuration

Open the settings.py file of our project and scroll to the database section. It looks like below one.

    DATABASES = {
        'default': {
            'ENGINE': 'django.db.backends.sqlite3',
            'NAME': BASE_DIR / 'db.sqlite3',
        }
    }


Update these settings with our PostgreSQL database details.

    DATABASES = {
        'default': {
            'ENGINE': 'django.db.backends.postgresql_psycopg2',
            'NAME': 'mydb',
            'USER': 'myuser',
            'PASSWORD': 'mypass',
            'HOST': 'localhost',
            'PORT': '',
        }
    }

## Verify the database connection

In the directory where `manage.py` script exists, run the below command.

    python manage.py migrate

If there are no errors, database migration will happen. Else errors will be displayed.
