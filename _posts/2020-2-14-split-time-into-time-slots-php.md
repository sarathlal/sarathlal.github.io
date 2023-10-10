---
title: Split time in to time slots - PHP
layout: post
tags:
  - PHP
---

If you need to split time into time slots with a proper time interval, you can use the below code snippet.

	function prepare_time_slots($starttime, $endtime, $duration){
		 
		$time_slots = array();
		$start_time    = strtotime($starttime); //change to strtotime
		$end_time      = strtotime($endtime); //change to strtotime
		 
		$add_mins  = $duration * 60;
		 
		while ($start_time <= $end_time) // loop between time
		{
		   $time_slots[] = date("H:i", $start_time);
		   $start_time += $add_mins; // to check endtime
		}

		return $time_slots;
	}

### Example

	$starttime = '9:00';  // your start time
	$endtime = '21:00';  // End time
	$duration = '30';  // split by 30 mins

	$time_slots = prepare_time_slots($starttime, $endtime, $duration);

	echo '<pre>';
	print_r($time_slots);
	echo '</pre>';

### Output

	Array
	(
		[0] => 09:00
		[1] => 09:30
		[2] => 10:00
		[3] => 10:30
		[4] => 11:00
		[5] => 11:30
		[6] => 12:00
		[7] => 12:30
		[8] => 13:00
		[9] => 13:30
		[10] => 14:00
		[11] => 14:30
		[12] => 15:00
		[13] => 15:30
		[14] => 16:00
		[15] => 16:30
		[16] => 17:00
		[17] => 17:30
		[18] => 18:00
		[19] => 18:30
		[20] => 19:00
		[21] => 19:30
		[22] => 20:00
		[23] => 20:30
		[24] => 21:00
	)
