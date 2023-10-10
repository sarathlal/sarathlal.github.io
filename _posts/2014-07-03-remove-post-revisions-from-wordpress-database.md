---
title: Remove Post revisions from WordPress Database
author: sarathlal
layout: post
tags:
  - WordPress
---
The post revisions are a feature in WordPress blog engine. When we edit or update a post or page, WordPress keep old data as a revision in WordPress database.

This is extremely helpful in certain situation because we can easily restore old data from these revisions.

But when we have more posts & pages in our blog, certainly we have a large database. Additional to these actual posts & pages, we have more than its double revisions in our database.

These stored post revisions don&rsquo;t have any direct impact on our WordPress performance until we have a large database. But keeping our database as small & optimized is a an important &ldquo;to do&rdquo; in such applications.

So now we are going to delete all our WordPress post revisions from database using a simple SQL command.

	DELETE FROM wp_posts WHERE post_type = "revision";

We can use MySQL command-line interface, phpMyAdmin, SQLyog or other MySQL GUI tools to perform this action. So use this tip & optimize our WordPress database to perform well.
