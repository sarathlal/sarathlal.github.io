---
title: Sanitize array using WordPress sanitization functions
layout: post
tags:
  - WordPress
---

Here is the array I need to sanitize.

    $array = array(
	    'key_1' => 'array elemnt 1',
	    'key_2' => 'array element 2'
    );

Now I need to sanitize array key & value using same sanitization function. If so, we can use `array_map` function.

    $new_array = array_map('sanitize_key', $array);

But some times, I need to sanitize array key & values using different sanitization functions.

    $array = array(
	    'key_1' => 'array elemnt 1',
	    'key_2' => 'array element 2'
    );

    $keys = array_keys($array);
    $keys = array_map('sanitize_key', $keys);

    $values = array_values($array);
    $values = array_map('sanitize_text_field', $values);

    $array = array_combine($keys, $values);

