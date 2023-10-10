---
title: A Bash script for automated WordPress backup
layout: post
tags:
  - WordPress
  - Server
  - Bash
---

In WordPress project, I believe that our main assets are database, custom theme files & plugin files. The backup means, securely keep this assets for future use.

In WordPress environment, there is too many options to back up the project. There is some amazing plugins & some hosting provider have separate package for backup handling.

But to familiarize with Bash, I have prepared a small script for WordPress backup. 

The script will backup our database, plugins files and theme files in monthly, weekly & daily manner. The backup will be stored in compressed format.

In monthly backup, our files & database are stored for 30 days. In each 30 days, files and database will be replaced with new one.

In weekly backup, files & database are stored in 7 days and replaced with new one in each 7 days period.

In daily backup, the last 3 days files & database are stored & all others will be deleted. That means total 5 backups in 5 separate time period & the risk will be minimal.

We have to create a cron job (Once in daily) in our server after uploading the Bash script to our server's `public_html` directory. The script will create a `backup` folder in `public_html` directory & the backups will be there.

*Note: I have tested the below script on a shared hosting environment and it works.*


	#!/bin/sh


	folder_to_backup="public_html/wp-content/themes public_html/wp-content/plugins"

	daily_backup="public_html/backup/daily"
	weekly_backup="public_html/backup/weekly"
	monthly_backup="public_html/backup/monthly"

	now=$(date +'%d-%m-%Y')

	yesterday=$(date -d "1 day ago" +'%d-%m-%Y')
	day_before_yesterday=$(date -d "2 day ago" +'%d-%m-%Y')
	day_before_seven_day=$(date -d "7 day ago" +'%d-%m-%Y')
	day_before_30_day=$(date -d "30 day ago" +'%d-%m-%Y')


	##### ##### ##### ##### ##### ##### ##### ##### ##### ##### ##### ##### #### 
	#			Clean and store daily backups
	##### ##### ##### ##### ##### ##### ##### ##### ##### ##### ##### ##### #### 

	#remove old backups from daily backup
	for i in $daily_backup/*
	do
		if [ $i = $daily_backup/$yesterday ] || [ $i = $daily_backup/$day_before_yesterday ]
		then
			echo "Match Found"
		else
			rm -rf $i
		fi
	done

	#create todays folder
	mkdir -p $daily_backup/$now

	#make daily backup
	tar -czf $daily_backup/${now}/wp-content.tar.gz $folder_to_backup/*


	##### ##### ##### ##### ##### ##### ##### ##### ##### ##### ##### ##### #### 
	#					Make Database backup
	##### ##### ##### ##### ##### ##### ##### ##### ##### ##### ##### ##### #### 
	config_file="public_html/wp-config.php"
	if [ -f "$config_file" ]
	then
		db_name=`cat public_html/wp-config.php | grep DB_NAME | cut -d \' -f 4`
		user=`cat public_html/wp-config.php | grep DB_USER | cut -d \' -f 4`
		password=`cat public_html/wp-config.php | grep DB_PASSWORD | cut -d \' -f 4`
		host=`cat public_html/wp-config.php | grep DB_HOST | cut -d \' -f 4`
		
		mysqldump --user=$user --password=$password --host=$host $db_name | gzip > $daily_backup/${now}/database.sql.gz
		
		if [ "$?" -eq 0 ]; then
			echo "Success"
		else
			echo "Error"
		fi
		
	fi



	##### ##### ##### ##### ##### ##### ##### ##### ##### ##### ##### ##### #### 
	#					Make weekly backup
	##### ##### ##### ##### ##### ##### ##### ##### ##### ##### ##### ##### #### 
	#Count weekly backup
	week_c=$(find $weekly_backup -mindepth 1 -type d | wc -l)

	#if weekly folder = 0, create one asap. Else check that it is 7 day ago, remove all backup and add a new one.

	if [ $week_c -eq 0 ]
	then
		
		mkdir -p $weekly_backup/${now}/
		cp -R $daily_backup/${now}/wp-content.tar.gz $weekly_backup/${now}/
		cp -R $daily_backup/${now}/database.sql.gz $weekly_backup/${now}/
		
	elif [  $week_c -eq 1  ]
	then

		week_name=$(find $weekly_backup -mindepth 1 -type d)

		if [ $week_name == $weekly_backup/$day_before_seven_day ]
		then
		
			#remove all directory 
			rm -rf $weekly_backup/*
			
			#make a copy of today archive
			mkdir -p $weekly_backup/${now}/
			cp -R $daily_backup/${now}/wp-content.tar.gz $weekly_backup/${now}/
			cp -R $daily_backup/${now}/database.sql.gz $weekly_backup/${now}/
		fi
		
	fi



	##### ##### ##### ##### ##### ##### ##### ##### ##### ##### ##### ##### #### 
	#					Make monthly backup
	##### ##### ##### ##### ##### ##### ##### ##### ##### ##### ##### ##### #### 
	#Count monthly backup
	month_c=$(find $monthly_backup -mindepth 1 -type d | wc -l)

	#if monthly folder = 0, create one asap. Else check that it is 30 day ago, remove all backup and add a new one.

	if [ $month_c -eq 0 ]
	then
		
		mkdir -p $monthly_backup/${now}/
		cp -R $daily_backup/${now}/wp-content.tar.gz $monthly_backup/${now}/
		cp -R $daily_backup/${now}/database.sql.gz $monthly_backup/${now}/
		
	elif [  $month_c -eq 1  ]
	then

		month_name=$(find $monthly_backup -mindepth 1 -type d)

		if [ $month_name == $monthly_backup/$day_before_30_day ]
		then
		
			#remove all directory 
			rm -rf $monthly_backup/*
			
			#make a copy of today archive
			mkdir -p $monthly_backup/${now}/
			cp -R $daily_backup/${now}/wp-content.tar.gz $monthly_backup/${now}/
			cp -R $daily_backup/${now}/database.sql.gz $monthly_backup/${now}/
		
		fi
		
	fi
	
I know that you have better ideas and option to make automated backups. I like to know more & if you have any suggestions, please [share with me](http://sarathlal.com/contact/).
