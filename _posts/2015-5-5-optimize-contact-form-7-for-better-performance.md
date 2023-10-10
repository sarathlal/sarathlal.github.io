---
title:  Optimize Contact Form 7 for Better Performance - WordPress
layout: post
tags:
  - WordPress
  - Page Optimization
---

The contact form 7 is one of the most used free plugin in WordPress. It is too simple & it works well with other WordPress plugins.

So instead of making custom contact forms, I like to use contact form 7 plugin in my WordPress site.

But same like other WordPress plugins, Contact Form 7 enqueued one CSS file and JavaScript file in all WordPress pages.

An extra CSS and/or JavaScript file on every page will be like extra baggage which we don't want to pick up when we are walking on foot. Two extra HTTP requests can negatively affect our site load time.

Basically we only want to load these CSS & JavaScript files only on the pages where we are using the Contact Form 7 plugin to create a form.

So now we are going to deregister contact form 7 styles and scripts on all pages except the page that we have contact forms.

### Deregistering Contact Form 7 CSS Files

Let's find the slug of our page with contact form. Go to Pages. Click Quick Edit and copy the slug.

Let's consider that we have a page titled "Contact Us" which has a URL slug contact-us. If so add the following code in our theme's functions.php file at the end.

	// deregister Contact Form 7 styles on all pages without a contact form
	add_action( 'wp_print_styles', 'contact_form_7_deregister_styles', 100 );
	function contact_form_7_deregister_styles() {
		if ( ! is_page( 'contact-us' ) ) {
			wp_deregister_style( 'contact-form-7' );
		}
	}

This code check that if the page is not `contact-us` then deregister the style CSS by Contact Form 7 for all the other pages.

### Deregistering Contact Form 7 JavaScript Files

	// deregister Contact Form 7 JavaScript files on all pages without a contact form
	add_action( 'wp_print_scripts', 'contact_form_7_deregister_javascript', 100 );
	function contact_form_7_deregister_javascript() {
		if ( ! is_page( 'contact-us' ) ) {
			wp_deregister_script( 'contact-form-7' );
		}
	}

This code check that if the page is not `contact-us` then deregister the JavaScript file by Contact Form 7 for all the other pages.

That's it. We removed two unnecessary HTTP requests on our pages & it will surely improve our page performance.

### If we have contact forms on multiple pages?

We are using `is_page()` function in our code snippet. We can add an array of pages as parameters on this function. It can get parameter value as Page ID, Page Title or Page Slug.

	is_page( array( ID, 'slug', 'Title' ) );

#### Example

	is_page( array( 42, 'about-me', 'Contact' ) );

This conditional tag will returns true when the Pages displayed is either post ID - "42", or page slug - "about-me", or Page title - "Contact".
