---
title: Get upcoming N days - PHP
layout: post
tags:
  - PHP
---

If you need upcoming N days in PHP, you can use the below code snippet.

	function get_upcoming_n_days($days, $format = 'Y-m-d'){
		$m = date("m"); $de= date("d"); $y= date("Y");
		$dateArray = array();
		for($i=0; $i<=$days-1; $i++){
			$dateArray[] = date($format, mktime(0,0,0,$m,($de+$i),$y)); 
		}
		return $dateArray;
	}

### Example

	$days = get_upcoming_n_days(7);
	
	echo '<pre>';
	print_r($days);
	echo '</pre>';

### Output

	Array {
		[0]=> 2020-02-14
		[1]=> 2020-02-15
		[2]=> 2020-02-16
		[3]=> 2020-02-17
		[4]=> 2020-02-18
		[5]=> 2020-02-19
		[6]=> 2020-02-20
	}

The default date format will be `Y-m-d`. To change that format, add format in the function call as the second parameter.
 
	$days = get_upcoming_n_days(7, 'd/m/Y');
