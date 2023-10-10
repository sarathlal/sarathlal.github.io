---
title: Dynamically create file in WordPress upload directory & make it as post attachment
layout: post
tags:
  - WordPress
---

Today, I need to create a text file in WordPress upload directory with dynamic content. Also need to set it as an attachment to a WordPress post.

Here is the quick function for this pourpose.

    function create_attachement($data, $post_id){
	    
	    $file_name = 'your_file_name.txt';
	    $upload = wp_upload_bits($file_name, null, $data);
	    if(!$upload['error']){
		    $wp_filetype = wp_check_filetype($file_name, null );
		    $attachment = array(
			    'post_mime_type' => $wp_filetype['type'],
			    'post_title' => preg_replace('/\.[^.]+$/', '', $file_name),
			    'post_content' => '',
			    'post_status' => 'private'
		    );
		    $attachment_id = wp_insert_attachment($attachment, $upload['file'], $post_id);
		    if($attachment_id){
			    //return $upload['url'];
			    return $attachment_id;
		    }

		    return false;
	    }
	    return false;
	    
    }

