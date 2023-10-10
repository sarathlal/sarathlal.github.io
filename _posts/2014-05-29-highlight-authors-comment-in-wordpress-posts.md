---
title: Highlight Author’s Comment in WordPress posts
author: sarathlal
layout: post
tags:
  - WordPress
---
Have you ever seen that post author comments have any differences between visitor comments in WordPress blogs. In default, WordPress serve both comments as in same manner in front end.

Now we are going to do a simple trick to mark Post author comment as different from other comments.

First we need to open `style.css` in our child theme. Then add some styles on it.

	.commentlist .bypostauthor, .commentlist li ul.children li.bypostauthor {
	background: #e7f8fb;
	}

When WordPress publish content, it generate some dynamic classes & ID with content. When publish comment, WP generate `bypostauthor` class for post author comments. We just want to style that class for an unique look. That is enough.

If we have multiple authors in our blog, even we can apply different styles for each and every authors by using dynamically generated `comment-author-author_name` class like below.

	.comment-list .comment.comment-author-your_author_name1 { }
	.comment-list .comment.comment-author-your_author_name2 { }
	.comment-list .comment.comment-author-your_author_name3 { }

Apply styles as per your intension & differentiate post author comment from other users comments in our WordPress blog. There is no any hard moments with this trick.
