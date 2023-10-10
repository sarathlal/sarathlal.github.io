---
title: 'Display all sites in a network as a drop down list &#8211; WordPress'
author: sarathlal
layout: post
tags:
  - WordPress
---
When creating WordPress network sites, regularly I want to display all sites in that network as a drop down in front end.

We can use a simple code snippet that use `wpdb` class to get such a list.

    <?php
    global $wpdb;
    $blogs = $wpdb->get_results($wpdb->prepare("SELECT * FROM $wpdb->blogs WHERE spam = '0' AND deleted = '0' and archived = '0' and public='1'"));
    if(!empty($blogs)){
     ?>
		 <select onChange="window.document.location.href=this.options[this.selectedIndex].value;" value="GO">
		 <?php
			 foreach($blogs as $blog){
			 $details = get_blog_details($blog->blog_id);
				 if($details != false){
					$addr = $details->siteurl;
					$name = $details->blogname;
						if(!(($blog->blog_id == 1)&&($show_main != 1))){ //This if statement that hide main site from list. So comment or uncomment this line with below closing tag
						?>
						<option value="<?php echo $addr; ?>"><?php echo $name;?></option>
						<?php
						} //End of if statement
				 }
			 }
		 ?>
		 </select>
     <?php
    }
    ?> 
