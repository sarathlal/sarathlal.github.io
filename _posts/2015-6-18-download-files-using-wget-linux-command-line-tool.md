---
title:  Download files using Wget - Linux command line tool
layout: post
tags:
  - Linux
  - Linux tools
  - Linux Commands
---

The Wget is a Linux command line utility to retrieving files using HTTP, HTTPS and FTP. It is a non-interactive command line tool, so it may easily be called from scripts, cron jobs, terminals without X-Windows support, etc.

The Wget can handle all most complex download situations including large file downloads, recursive downloads, non-interactive downloads, multiple file downloads etc.

During server management sessions, often I want to use this linux tool. So now I just like to review few download method examples using Wget in different scenarios.

#### 1) Download file to current folder with same name

	wget your-download-file-link

#### 2) Download file to current folder with different name using Wget `-O`

	wget -O new-file-name your-download-file-link

#### 3) Download in the Background Using Wget `-b`

For a huge download, we can make the download as a background action.

	wget -b your-download-file-link

#### 4) Download Multiple items Using Wget `-i`

First we are going to make a text file that contain all URLs for download items using `cat` command.

	cat > new.txt
	
This awaits input from user, so type the urls and then use `CTRL+D` to save and exit.

	cat > new.txt
	url1
	url2
	url3
	
Next, give the `new.txt` as argument to wget using `-i` option as shown below.

	$ wget -i new.txt
	
#### 5) Specify Download Speed Using Wget `--limit-rate`

In some situations, we want to limit the Download speed. So we just want to use `--limit-rate` option and its value with `wget` command.

	wget --limit-rate=200k your-download-file-link
	
#### 6) Increase Total Number of Retry Attempts Using Wget `--tries`

If the size of the file to be downloaded is larger, there is a chance of failures in the download. But default `wget` retries 20 times to make the download successful. 

If needed, we can increase retry attempts using `--tries` option as shown below.

	wget --tries=75 your-download-file-link
	
