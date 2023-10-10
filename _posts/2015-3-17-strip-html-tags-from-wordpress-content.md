---
title: Strip HTML tags from WordPress Content
layout: post
tags:
  - WordPress
---

The WordPress have a default function to properly strip all HTML tags including script and style from its content.

	<?php wp_strip_all_tags( $string, $remove_breaks ); ?>


#### Parameters

1. $string:- (required) String containing HTML tags (Default: None)
2. $remove_breaks:- (boolean) (optional) Whether to remove left over line breaks and white space characters (Default: false)


### example:

	<?php
	$html = '<strong>I am not be strong</strong>';
	var_dump($html);
	//ouput '<strong>I am not be strong</strong>'

	var_dump(wp_strip_all_tags($html));
	//ouput 'I am not be strong'
	?>
