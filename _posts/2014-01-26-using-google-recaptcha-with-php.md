---
title: Using Google reCAPTCHA with PHP
author: sarathlal
layout: post
tags:
  - PHP
  - reCAPTCHA
---
The reCAPTCHA is a Google captcha service & it is widely used on website & blogs to prevent spam comments & automated extraction of data from websites.

Today we are going to use reCAPTCHA service in our PHP web application to familiarize with reCAPTCHA & its usage.

Before implementing reCAPTCHA, just know that it was started as a college project in Carnegie Mellon University&#8217;s Pittsburgh campus, and acquired by Google in September 2009.

The user submitted text are used to digitize books and building machine learning datasets. More than 200 million ReCaptcha&rsquo;s are entered every day and that relates to about 150,000 man hours of work!

Anyway, if we want to use reCAPTCHA, first we want to [sign up][1] for reCAPTCHA service. We can use our Google account for this purpose.

After sign up, just add our domain name. Then the reCAPTCHA service will generate some special keys for us. The reCAPTCHA only works on our specified domain & its sub domains only.

By default, all keys work on `localhost` (or `127.0.0.1`). So for testing purpose, if we don&#8217;t have a domain name yet, we can use a demo domain name.

Before any further steps, note down our special keys for our domain. They are known as public & private keys. We want to use them in next steps.

To simply use reCAPTCHA with PHP, we want to download reCAPTCHA PHP library from [here][2]. We only need a single file (`recaptchalib.php`) from that collection.

##  Client Side &#8211; How to make the CAPTCHA image show up

Normally we use captchas in forms & user submissions. So to display reCAPTCHA in a form, we want to insert a small snippet of code inside the `<form>` element where the reCAPTCHA widget will be placed.

	require_once('recaptchalib.php');
	$publickey = "our_public_key"; // we got this from the signup page
	echo recaptcha_get_html($publickey);

In this code snippet, first line include our downloaded PHP `recaptchalib.php`. The second line is about our public key. Just copy paste our public key at there.

Now our HTML form in PHP page look like below one.

	<form method="post" action="verify.php">
		<?php
		  require_once('recaptchalib.php');
		  $publickey = "your_public_key"; // you got this from the signup page
		  echo recaptcha_get_html($publickey);
		?>
		<input type="submit" />
	</form>

##  Server Side &#8211; How to test if the user entered the right answer

In our form, the target to submit data is `verify.php`. So we add another snippet of code at the top of our form target file.

	<?php
	require_once('recaptchalib.php');
	$privatekey = "our_private_key";
	$resp = recaptcha_check_answer ($privatekey,
								$_SERVER["REMOTE_ADDR"],
								$_POST["recaptcha_challenge_field"],
								$_POST["recaptcha_response_field"]);

	if (!$resp->is_valid) {
	  // What happens when the CAPTCHA was entered incorrectly
	  echo "You are not human!";
	} else {
	  // our code here to handle a successful verification
	  echo "You are verified as human!";
	}
	?>

For simplicity, I just echo a message according to verification. We want to replace that messages with our actual code to be happened after verification.

Try this on our localhost & surely it will help us in our upcoming projects.

 [1]: https://www.google.com/recaptcha/admin#whyrecaptcha
 [2]: http://code.google.com/p/recaptcha/downloads/list?q=label:phplib-Latest
