---
title: Self submit a form values using PHP_SELF
author: sarathlal
layout: post
tags:
  - PHP
---
In some cases, we want to submit some form data in web pages to itself. We can achieve this by using `PHP_SELF` variable in action field of the form.

This `PHP_SELF` variable returns the name and path of the current file. So when we use `PHP_SELF` variable in action field of the form, form values are submitted to same page.

Through this post, we are making a simple page to understand the use of the `PHP_SELF` variable. This page has some basic form field & when user submit the form values, it will produce a welcome message for the user.

In our page, we have HTML & PHP code. So we name our file as `welcome.php`. Now first we can create form handler script in our page that will welcome our user.

	<?php
		if(isset($_POST['submit']))
		{

			echo "Welcome ". $_POST["name"]."<br>";
			echo "Your email address is: ". $_POST["email"]."</br>";
		}
	?>

In our form handler script, we add an `if` statement to check the status of submit button. Using this `if` statement, our PHP script only display a welcome message after the user submit the form value.

Now we can add our HTML form in this same page.

	<form method="post" action="<?php echo $_SERVER['PHP_SELF']; ?>">
		Name: <input type="text" name="name"><br>
		E-mail: <input type="text" name="email"><br>
		<input type="submit" value="submit">
	</form>

Have you noticed the action in our HTML form? It utilize the `PHP_SELF` variable & thus the form values are submitted to same page. So after the form submission, the form data are available on the same page.

*But when we use `PHP_SELF` variable in our form&#8217;s action, it will open a door for hackers. We want to understand & avoid this exploit. You can read about a normal practice to escape from this vulnerability from [here][1].*

 [1]: http://sarathlal.com/understand-avoid-php-self-exploit.html
