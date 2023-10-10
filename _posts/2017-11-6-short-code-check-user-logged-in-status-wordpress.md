---
title: Short code to check user logged in status - WordPress
layout: post
tags:
  - WordPress
---

In some WordPress project, we need to restrict content on the page as per user logged in stataus. If we are customizing template files to display content, we can easily restrict content by checking user logged in status using `is_user_logged_in()` function.

Same way, if we need to restrict content on content area, we can use below code snippets & short codes.

## Display content for visitors only 

#### Code snippet

	add_shortcode( 'visitor', 'visitor_check_shortcode' );
	function visitor_check_shortcode( $atts, $content = null ) {
		 if ( ( !is_user_logged_in() && !is_null( $content ) ) || is_feed() )
			return $content;
		return '';
	}

#### Short code

	[visitor]
	Some content for the people just browsing your site.
	[/visitor]

## Display content for logged in users only

#### Code snippet

	add_shortcode( 'member', 'member_check_shortcode' );
	function member_check_shortcode( $atts, $content = null ) {
		 if ( is_user_logged_in() && !is_null( $content ) && !is_feed() )
			return $content;
		return '';
	}

#### Short code

	[member]
	This is members-only content.
	[/member]
