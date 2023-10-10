---
title: Make a WordPress child theme to learn basics
author: sarathlal
layout: post
tags:
  - WordPress
---
A WordPress child theme is a theme that inherits property of another WordPress theme, called parent theme. Using this child theme, we can modify looks and functions with additional little coding in child theme files.

We can consider child theme as a support system for our parent WordPress theme. Every one like there website in different looks and feels. That means customization. I believe that easiest and safest way to customize our WordPress installation is child theme.

##  Advantages of Child theme

*   We are doing modifications in our child theme to customize parent theme. So if when a update is become available for parent theme, it never alter our WordPress looks and functions.
*   If we have a non edited WordPress default theme, it help us in some critical situations.
*   Child theme is a copy of parent theme with inherited properties of parent theme. So we have a frame work. It is our parent theme. We just modify our parent theme with our imagination. It avoid the pain of beginning from scratch.
*   If we are choosing default and popular WordPress themes as our parent theme, A to Z modifications are available in different websites and forums etc. We just want to copy and edit these codes for our custom WordPress.

##  STEP 1: Create a folder for child theme

In our WordPress installation, We have three folders ( `wp-admin`, `wp-content` and `wp-includes` ) and some php files. Now consider that we are making a child theme for WordPress new default theme, `Twenty Thirteen`.

*   First open `wp-content` folder
*   Then open `themes` folder inside `wp-content`
*   Make a new folder inside `theme` folder
*   Rename it as `twentythirteen-child`

This is a common practice in WordPress child theme development. Rename directory with out any space and use the name of parent theme with a `-child` appended to it like `twentyten-child`, `twentyeleven-child` and `twentytwelve-child` etc.

##  STEP 2: Create essential file for child theme

*   Inside child theme folder, create a new text file and rename it as style.css. This is the only file required to make a child theme.
*   Copy and paste below code in to beginning of style.css

		 /*
		Theme Name:     Twenty Thirteen Child
		Theme URI:      http://yourdomain.com/
		Description:    Child theme for the Twenty Thirteen theme
		Author:         Your name here
		Author URI:     http://yourdomain.com/about/
		Template:       twentythirteen
		Version:        0.1.0
		*/

This is the introduction code for our WordPress child theme. We can change, any lines in this code according to our theme. The only lines required are Theme name and Template.

The theme name is our child theme name. Give a meaning full name for it like Twenty Thirteen Child etc. Then Template is our parent theme folder ( directory ) name.

If our Parent theme folder have a name `me`, then your template is also `me`. In our article, my parent theme is Twenty Thirteen theme and it is in a folder called `twentythirteen`. So I give my template name as `twentythireen`.

*   Copy and paste below code in to the style.css

<div>
@import&lt;/span> &lt;span>url&lt;/span>&lt;span>(&lt;/span>&lt;span>"../twentythirteen/style.css"&lt;/span>&lt;span>)&lt;/span>&lt;span>;&lt;/span>
</code></pre>
</div>

Through our child theme, we are doing modifications in our parent theme. So we want to inherit style properties of parent WordPress theme in to our child theme. The above line of code do this action in our child theme.

*   Save style.css

*Note: `style.css` in child theme just override `style.css` in parent theme folder. So all other unchanged css properties are inherited from parent theme.*

##  STEP 3: Activate child theme from admin panel

*   Go to your administration panel >> Appearance >> Themes.
*   Now you can find a new theme named as Twenty Thirteen Child. Activate this child theme

##  STEP 4: Add additional files for child theme

In STEP 2, we make a style sheet &#8211; `style.css` in our child theme directory. It is the only essential file for a child theme. But it is not a complete child theme. The `style.css` can only handle style properties ( CSS properties ) of WordPress. So to improve our theme&#8217;s functions, we can add a `functions.php` in our child theme directory.

In our parent theme folder, there is also a `functions.php`. This `functions.php` is responsible for parent WordPress theme functions. If we have additional PHP functions or we want to edit current functions, we can use our child theme&#8217;s `functions.php` file.

*   Create a new file in our child theme folder and rename it as `functions.php`.
*   Structure of `functions.php` is simple. It only require an opening PHP tag at the beginning. After this opening PHP tag, we can add our bits of PHP code.
    
		<?php

*Note: Unlike `style.css` in child theme, `functions.php` in child theme does not override `functions.php` in parent theme. It is loaded with the parent `functions.php` file as a additional `functions.php` file.*

##  STEP 5: Add template files in to child theme

The `style.css` and `functions.php` can do almost customization of our WordPress theme. But in almost cases, we want to modify our template files. The template files control and present our content in database and PHP file as web pages.

Just realize that, our archive page have different look than home page. Also our Header is beautiful than our footer because these every page or section have different template files in your parent theme.

So in some cases, we need to edit these template files. In order to avoid the editing of parent theme files, we just copy these template files in to our child theme. So if we want to modify our header template, copy `header.php` from parent theme folder and paste it in to child theme folder. Then we can modify our `header.php` in child theme folder as per our requirement.

*Note: header.php, footer.php, index.php, content.php, archive.php, page.php, single.php, category.php etc are the main template files used in WordPress themes. Each file have there own functions and design.*

##  Upload WordPress Child theme from our computer

If you are unfamiliar with C Panel, You can do all this action by making a folder in your computer with your child Theme name. Then after all basic structuring, compress that folder ( .zip format ) and upload it in to your WordPress theme directory using administration Panel.

Go to Administration panel >> Appearance >> Themes.

There is two tabs at top to manage themes and install themes. Select Install Themes, there is a upload option. We can upload compressed themes ( in .zip format ) using this feature.

##  Edit WordPress Theme files

If you are familiar with C Panel, you can easily add, remove and edit WordPress files including theme files from there directory. Go to wp-content >> themes >> Your theme.

Else you can easily edit WordPress theme files from editor in administrator Dashboard. Go to Administration panel >> Appearance >> Editor.

In Theme editor, we can select theme and files to edit. Then after editing, always remember to update theme by clicking *Update File* button at bottom.
