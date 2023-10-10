---
title: Handle custom form in WordPress
layout: post
tags:
  - WordPress
---

Have you ever tried custom forms in WordPress. It is too easier than you think.

Here is my sample form.

	<form method='post' action=''>
		<input name='name' type='text' value='' />
		<?php echo wp_nonce_field('handle_custom_form', 'nonce_custom_form'); ?>
		<input type='submit' value='Submit'/>
	</form>

Form handling function for sample form is given below. Always strictly validate form fields.

	public function wpsa_handle_custom_form()
	{
		if (!empty($_POST['nonce_custom_form']))
		{
			if (!wp_verify_nonce($_POST['nonce_custom_form'], 'handle_custom_form'))
			{
				die('You are not authorized to perform this action.');
			} else
			{
				$error = null;
				if (empty($_POST['name']))
				{
					$error = new WP_Error('empty_error', __('Please enter name.', 'your-text-domain'));
					wp_die($error->get_error_message(), __('CustomForm Error', 'your-text-domain'));
				}
				else
				{
					die('Its safe to do further processing on submitted data.');
					//Process submitted data from here
					//$name = $_POST['name'];
				}
			}
		}
	}

	add_action('init', 'wpsa_handle_custom_form');
