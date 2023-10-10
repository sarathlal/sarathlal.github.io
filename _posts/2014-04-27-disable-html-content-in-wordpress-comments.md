---
title: Disable HTML content in WordPress comments
author: sarathlal
layout: post
tags:
  - WordPress
---
The post comments is consider as a method to increase user interaction in our blogs. When we read certain articles, we can realize that the comments associated with that article have more quality than the content.

But if we have poor comment moderation methods, spammers utilize this commenting system to increase there site SEO by inserting there links in our post comments.

In WordPress, we have amazing plugins and method to avoid automatically generated spam comments. But they have limitations & we want to do manual moderation in almost cases.

In spam comments, we can realize that they are always associated with a web address. They write spam comments in our post comments because they can create HTML links via there comments.

So today we are going to tighten our comments terms & policy. From now, we never allow HTML content in our post comments.

All you have to do is simply open our child theme&#8217;s `functions.php` and add the following code.

	// This will occur when the comment is posted
	function plc_comment_post( $incoming_comment ) {

	// convert everything in a comment to display literally
	$incoming_comment['comment_content'] = htmlspecialchars($incoming_comment['comment_content']);

	// the one exception is single quotes, which cannot be #039; because WordPress marks it as spam
	$incoming_comment['comment_content'] = str_replace( "'", ''', $incoming_comment['comment_content'] );

	return( $incoming_comment );
	}

	// This will occur before a comment is displayed
	function plc_comment_display( $comment_to_display ) {

	// Put the single quotes back in
	$comment_to_display = str_replace( ''', "'", $comment_to_display );

	return $comment_to_display;
	}

This code snippet will filter HTML from our comments. If spammers can&#8217;t link there website, they like to avoid our posts because there intension is only simple link generation.
