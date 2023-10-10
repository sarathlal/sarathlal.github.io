---
title: Handling form using AJAX in WordPress
layout: post
tags:
  - WordPress
---

As a WordPress developer, regularly I need to use forms in WordPress front end & admin pages. I like to use AJAX for form submissions because it will avoid page redirection & AJAX improves user interactions.

So here is the HTML, Javascript & PHP code collection that I use normally in my plugins. Sorry, there is no detailed explanation.

### HTML FORM

    <form name='sample_form' method='post' id='sample_form'>
        <p>
		    <label for="user_name">User name</label>
		    <input type='text' name="user_name" />
	    </p>
	    <p>
		    <input type='submit' class='button' value='submit' />
		    <input type="hidden" name="action" value="prefix_your_action_name">
		    <?php wp_nonce_field( 'name_of_my_action', 'name_of_nonce_field' ); ?>	
	    </p>
    </form>

You have to display the form in WordPress pages using proper hooks.

### JavaScript / jQuery

    $('#sample_form').submit(function(e){
        e.preventDefault();
	    var formData = form.serializeArray();
	    $.ajax({
		    type: 'POST',
		    url : ajaxurl, // `ajaxurl` only available in admin end
		    data: formData,
		    beforeSend : function(){
			    // action before submit
		    },
		    success: function(response){
			    // On success
		    },
		    error: function(jqXHR, textStatus, errorThrown){
			    // On error
		    },
		    complete: function(jqXHR, textStatus){
			    // On complete
		    }
	    });
    });

### PHP / WordPress

    // Fires authenticated Ajax actions for logged-in users.
    add_action( 'wp_ajax_prefix_your_action_name', 'your_callback_function' );

    // Fires non-authenticated Ajax actions for logged-out users.
    add_action( 'wp_ajax_nopriv_prefix_your_action_name', 'your_callback_function' );

    function your_callback_function(){
	    if(!isset($_REQUEST['name_of_nonce_field']) || !(wp_verify_nonce($_REQUEST['name_of_nonce_field'], 'name_of_my_action'))){
	       wp_die('error!');
	    }else{
	       // process form data
	    }

	    wp_send_json($your_result);
    }
