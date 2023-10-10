---
title: Simple spam protection on contact forms using hidden input field
author: sarathlal
layout: post
tags:
  - SPAM Protection
  - PHP
---

If we have contact forms in website, the spam mails will be the most annoying things in our inbox.

But using a simple hidden input fields, we can escape from almost spam bots.

Now we are going to make a contact form with a hidden input field. We like to hide this input field using CSS. So a normal user never seen this input field and even if the CSS fails to load, they get a note explaining what to do.

But in general, bots struggle with reading CSS or JavaScript. So when a spam bot looks at this, it sees a good spot to stick whatever spammy url they’re trying to advertise.

In server-side, before doing any actions on this contact form, we will check the value of that hidden input field. If there is a value, that means this contact request was submitted by a spam bots and we will throw it out.

### The HTML

	<form action="/submit.php" method="post">
		<p>Your name: <input type="text" name="name" /></p>
		<p>Your email: <input type="text" name="email" /></p>
		<p style="display:none;">Leave this empty: <input type="text" name="url" /></p>
		<p><textarea name="message"></textarea></p>
		<p><input type="submit" value="Send" /></p>
	</form>

### The PHP

	<?php
	// if the url field is empty 
	if(isset($_POST['url']) && $_POST['url'] == ''){
		 // then send the form to your email

	} else {
		// Do some actions for spam bot
	}
	?>


Now the PHP script on the server can tell who is a spammer and who isn’t. The regular people can sent contact request & the spammers get ignored! That is enough.
