---
title: Handle a basic HTML form with PHP
author: sarathlal
layout: post
tags:
  - PHP
---
The HTML forms are widely used in websites and web applications. They help us to collect information from users and deliver appropriate result from server.

The HTML forms are basic user interfacing. With these HTML forms, we want to use some server-side scripting language to talk with servers. The PHP is a powerful server-side scripting language & it is widely used in web applications.

Through this post, we are making a basic HTML form, collect some data from our user & deliver appropriate result from server with the help of PHP.

###  Step 1: Create a HTML form

To talk with server, now we are making a basic HTML forms. They have two text fields & a submit button. When we press the submit button, our values in text field are submitted in to `welcome.php` page in server & it display a welcome screen.

	<html>
		<body>
		 <form action="welcome.php" method="post">
			Name: <input type="text" name="name"><br>
			E-mail: <input type="text" name="email"><br>
			<input type="submit" value="submit">
		 </form>
		</body>
	</html>

Our HTML form is very easy to understand. It ask our name & Email address. Then it submit our values in to `welcome.php` via `POST` method.

###  step 2: Create a PHP page to welcome our visitors

To process these collected values, we want to create a PHP page. In our HTML form, we already tell that we are going to use `welcome.php` as the action of that form.

So now we are going to create a basic PHP page, `welcome.php` to welcome our visitors.

	<html>
		<body>
		Welcome <?php echo $_POST["name"]; ?><br>
		Your email address is: <?php echo $_POST["email"]; ?>
		</body>
	</html>

In our PHP page, we only use basics functions. The `echo` is not a PHP function, it is a language construct. To get output from PHP page, we use this `echo`.

If you want to print `Hello` from a PHP page, you just want to `echo` this `Hello` like `<?php echo "Hello"; ?>`. The `<?php` is the opening tag & `?>` is the closing tag in PHP.

If we want to print the value of a variable, we want to `echo` that variable like `<?php echo $my_variable; ?>`.

In our `welcome.php` page, we `echo` two variable, `$_POST["name"]` & `$_POST["email"]`. The `$_POST` is a global variable & the name of our HTML form fields will automatically be the keys in the `$_POST` array.

In our HTML form, the name of form fields are `name` & `email`. So our keys in `$_POST` array are `name` & `email`. We can access the value of form fields like `$_POST["key"]` and then we display its values using `echo`.

The output will be a welcome screen that welcome our user with his name & email.

	Welcome sarath
	Your email address is: claa@cloo.com

Anyway, this is a basic form handling in PHP & I have to learn more.
