---
title:  Encrypt Email Addresses - PHP
layout: post
tags:
  - PHP
---

### The Function

	function encode_email($e) {
		for ($i = 0; $i < strlen($e); $i++) { $output .= '&#'.ord($e[$i]).';'; }
		return $output;
	}

### Usage

	echo(encode_email('user@example.com'));

[Source](https://davidwalsh.name/php-email-encode-prevent-spam){:target="_blank"}
