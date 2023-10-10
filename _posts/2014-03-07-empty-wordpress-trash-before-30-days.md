---
title: Empty WordPress trash before 30 days
author: sarathlal
layout: post
tags:
  - WordPress
---
In WordPress, when we delete posts, pages & comments, WordPress will keep all of these items in trash for next 30 days. Else we want to go to trash & permanently delete them.

After 30 days, WordPress will delete all trashed items. But if these items are unnecessary for 30 days, why we want to keep them in our database?

Now we are going to reduce these 30 days life time of trashed items using a single line of code.

Add the below line of code in `wp-config.php` in our root folder.

	define ('EMPTY_TRASH_DAYS', 7);

From now, WordPress will empty its trash items after 7 days.

If you like to completely disable trash in WordPress, we can choose zero days like below.

	define ('EMPTY_TRASH_DAYS', 0);
