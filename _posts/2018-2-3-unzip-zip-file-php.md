---
title: Unzip zip file using PHP
layout: post
tags:
---

When I move some application to servers, in some rare cases, client server was little difficult to manage. The GUI was very messy or missing & there is no SSH access.

Normally we upload files & folders in zip format to improve speed. Also if we upload zip files, there is very less chance for file / folder missing.

After uploading, I need to extract the content without GUI & SSH access. Below you can find few methods that help me to solve the problem.

### Using PHP built-in extensions

	$zip = new ZipArchive;
	$res = $zip->open('file.zip');
	if ($res === TRUE) {
	  $zip->extractTo('/myzips/extract_path/');
	  $zip->close();
	  echo 'Done!';
	} else {
	  echo 'Failed!';
	}

Note: If you need to extract in the same directory, use `getcwd()` function to get current path.

	//$zip->extractTo('/myzips/extract_path/');
	$zip->extractTo(getcwd());

### Using Unix unzip command

	<?php system('unzip wordpress.zip'); ?>
