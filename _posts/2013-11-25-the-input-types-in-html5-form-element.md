---
title: The input types in HTML5 form element
author: sarathlal
layout: post
tags:
  - HTML5
---
From a decade, HTML form has some common input types & some attributes for them. We widely used them in our applications & all browsers support them.

I just list out the input types available in HTML4 form element at here for a reference.

1.  Checkbox
2.  Radio button
3.  Password field
4.  Drop-down list
5.  File selection
6.  Submit button
7.  Text field

We don&#8217;t need an explanation about these form inputs because we are regularly using them in our daily life. In our contact forms & online application pages, we are using these input types.

In HTML5, We have an improved Form element. Now we have more than a dozen new input types and too many new attributes for them. Today, I&#8217;m going to explore this new input types in HTML5 form element.

| Input Type       | Description                                                                                                                                                                                  |
| ---------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `url`            | To enter a URL, we can use `url` input type. It must start with a valid URI scheme (like http://, ftp:// or mailto: etc).                                                                    |
| `tel`            | The `tel` is usable to enter phone numbers. It does not enforce a particular syntax for validation, so if we want to ensure a particular format, we need to use `pattern` attribute with it. |
| `email`          | For entering email addresses. By default it will only take one, but if the multiple attribute is provided, a comma separated list of email addresses is valid.                               |
| `search`         | A text input field styled in a way that is consistent with the platform&#8217;s search field.                                                                                                |
| `number`         | For numeric input, can be any rational integer or float value. It support attribute like `min`, `max`, `step` & `value` etc. We can make it as a spin box with these attributes.             |
| `color`          | It help us to pick a color and returns the color&rsquo;s hexadecimal representation.                                                                                                         |
| `range`          | It is also used for number input, but unlike the number input type, the value is less important. It is displayed to the user as a slider control.                                          |
| `datetime`       | Used to enter a date and time value where the time zone is provided as GMT.                                                                                                                  |
| `datetime-local` | For entering a date and time value where the time zone provided is the local time zone.                                                                                                      |
| `date`           | For entering a date (only) with no time zone provided.                                                                                                                                       |
| `time`           | For entering a time (only) with no time zone provided.                                                                                                                                       |
| `week`           | For entering a date that consists of a week-year number and a week number, but no time zone.                                                                                                 |
| `month`          | For entering a date with a year and a month, but no time zone.                                                                                                                               |

##  The benefits of these new input types

This new input types give some hints to the web browser about what type of keyboard layout to display for on-screen keyboards.

Also the modern browsers can provide built-in validation for some input types like email and url. On other elements, we can indicate a valid input format by providing a regular expression in the the `pattern` attribute.

We can find various applications with these new input types. Already it have power to replace JavaScript code for form validation etc. But we need a updated & modern browser.

Any way, these input types will help to make beautiful & user friendlier web forms in feature days. We want to play more with them to get our hands dirty.
