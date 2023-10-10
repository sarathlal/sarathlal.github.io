---
title: Display upcoming posts in WordPress
author: sarathlal
layout: post
tags:
  - WordPress
---
Some of us often schedule some post for upcoming days. This is more occurred in magazine style blogs.

If our clients have such a nature, we can create an upcoming posts list in there page or sidebar. This will make readers look forward to what they are going to publish in a few days and can help to get new RSS subscribers.

	<div id="future_posts">
		<div id="future_posts_header"><p>Future Posts</p></div>
		<?php query_posts('showposts=10&post_status=future'); ?>
		<?php if ( have_posts() ) : while ( have_posts() ) : the_post(); ?>
			<div >
				<p class><b><?php the_title(); ?></b><?php edit_post_link('e',' (',')'); ?><br />
				<span class="datetime"><?php the_time('j. F Y'); ?></span></p>
			</div>
		<?php endwhile; else: ?><p>No future posts scheduled.</p><?php endif; ?>
	</div>

We just use WordPress `query_posts()` function at here. In this code snippet, this function retrieve 10 posts with the post status `future`. If this query can't find any future posts, it return an error message.
