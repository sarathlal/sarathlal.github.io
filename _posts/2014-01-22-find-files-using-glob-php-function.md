---
title: 'Find files using glob() - PHP function'
author: sarathlal
layout: post
tags:
  - PHP
---
The glob() is a default PHP function & it can act as a variant of `scandir()` with more capability. It can find files that matching a pattern.

The glob() returns an array containing the matched files/directories and an empty array if no file matched or FALSE on error.

	// get all php files
	$files = glob('*.php');

	print_r($files);

The output will be

	Array
	(
		[0] => myphp.php
		[1] => me.php
		[2] => page_output.php
	)

We can also fetch multiple file types using glob().

	// get all php files AND txt files
	$files = glob('*.{php,txt}', GLOB_BRACE);

	print_r($files);   

The `GLOB_BRACE` is a flag in `glob()` function used to expand {a,b,c} to match &#8216;a&#8217;, &#8216;b&#8217;, or &#8216;c&#8217;.

Now the output will be a collection of file names with `.php` & `.txt` extension.

	Array
	(
		[0] => myphp.php
		[1] => me.php
		[2] => page_output.php
		[3] => log.txt
		[4] => test.txt
	)

We can also return file name with its path by just improving our query.

	// find files from image directory
	$files = glob('../image/a*.jpg');

	print_r($files);

The result will be,

	Array
	(
		[0] => ../image/apple.jpg
		[1] => ../image/art.jpg
	)

If we want the full path to each file, we can just call the `realpath()` function on the returned values.

	$files = glob('../image/a*.jpg');

	// applies the function to each array element
	$files = array_map('realpath',$files);

	print_r($files);

Now the result will be full path of each file that match `glob()` pattern.

	Array
	(
		[0] => varwwwimageapple.jpg
		[1] => varwwwimageart.jpg
	)
