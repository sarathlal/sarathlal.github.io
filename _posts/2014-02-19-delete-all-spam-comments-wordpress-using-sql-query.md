---
title: Delete all spam comments in WordPress using SQL query
author: sarathlal
layout: post
tags:
  - WordPress
---
When I start to deal with WordPress for clients, always some of them complaint about spam comments. We can use some Spam protection plugins to control spam.

But if a real human being type his promotional words & links in comments, we have limitations. We want to manually mark it as spam to protect our blog.

When we mark comment as spam, they are still in our database. So now we are going to remove these unwanted spam from our database using a simple SQL query.

	DELETE FROM wp_comments WHERE comment_approved = 'spam';

Try this query & help to keep our database as optimized.
