---
title: List our most commented posts as popular posts in WordPress
author: sarathlal
layout: post
tags:
  - WordPress
---
What is your opinion about popular posts widget in Blogs? They have any benefits in user interactions?

The popular posts list have certain values in blogs. Surely this list indicate that we keep a good community around us.

When we list our popular posts, I think new visitors can easily grab the spirits of our blog community because our readers make our popular posts.

In WordPress, we have too many good plugins to make such lists. But as a WordPress developer, I always like to use code snippets for such simple use.

Can we consider number of comments in post as an indication for popularity? If so, now we are going to make a popular posts list by listing most commented posts in our blog.

Just paste the following code anywhere in your theme files or make a new function & call it on theme files. To change the number of displayed posts, simply change the &ldquo;5&Prime; on line 3 to your desired number.

	<h2>Popular Posts</h2>
	<ul>
		<?php $result = $wpdb->get_results("SELECT comment_count,ID,post_title FROM $wpdb->posts ORDER BY comment_count DESC LIMIT 0 , 5");
		foreach ($result as $post) {
		setup_postdata($post);
		$postid = $post->ID;
		$title = $post->post_title;
		$commentcount = $post->comment_count;
			if ($commentcount != 0) { ?>

			<li><a href="<?php echo get_permalink($postid); ?>" title="<?php echo $title ?>">
			<?php echo $title ?></a> {<?php echo $commentcount ?>}</li>
		<?php } } ?>

	</ul>

This code executes an SQL query to the WordPress database, using the `$wpdb` object, to get a list of the five posts with the most comments. The results are then wrapped in an unordered HTML list.
