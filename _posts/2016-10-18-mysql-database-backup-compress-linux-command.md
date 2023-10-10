---
title: Create MySQL database backup using `mysqldump` - Linux Command
layout: post
tags:
  - Linux
  - Server
  - MySql Server
  - Linux Commands
---

The `mysqldump` is a nice utility to performs logical backups that producing a set of `SQL` statements that can be executed to reproduce the original database object definitions and table data.

The result of `mysqldump` is a flat text file & normally the size of the resulted file is little big. If we compress such text files, we can achieve good compression rates & it help to reduce our disk space usage.

	mysqldump --user=$user --password=$password --host=$host $db_name > database.sql
	gzip -v database.sql


If you like to compress database on the fly with only one command, check the below command.

	mysqldump --user=$user --password=$password --host=$host $db_name | gzip > $daily_backup/${now}/database.sql.gz

This might be useful in situations where space is a problem and the full dump can’t be saved on the available storage directly because of its size.
