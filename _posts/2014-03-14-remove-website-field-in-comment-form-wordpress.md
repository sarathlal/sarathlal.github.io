---
title: 'Remove website field in comment form &#8211; WordPress'
author: sarathlal
layout: post
tags:
  - WordPress
---
The website field in comment form in blogs and CMS help comment authors to make a link towards there website / blog. This is a normal practice to increase traffic towards there website / blog. It help us and them because the number of valuable comments in our article is now consider as a measure of quality of content.

If the comments are valuable for that content and readers, there is a chance to get referral traffic towards the comment authors website / blog. But spammers always utilize this facility to make pure back linking to there website / blog using keywords in comments.

Any way we can easily remove website field in WordPress comment form if it is not necessary.

*   First we want to open child theme&#8217;s function.php file.*
*   Copy and paste below code snippet to child theme&#8217;s function.php file.

		add_filter('comment_form_default_fields', 'url_filtered');
		function url_filtered($fields)
		{
		  if(isset($fields['url']))
		   unset($fields['url']);
		  return $fields;
		}

*   Save file, logout from administration panel and check weather website field is available in post comment form.

###  Remarks

*Before starting, you need a WordPress child theme and necessary files for it. I already write a post about how we can create a child theme for WordPress in simple steps.
