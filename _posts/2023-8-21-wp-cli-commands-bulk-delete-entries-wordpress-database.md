---
title: WP CLI Commands to Bulk Delete Entries in WordPress Database
layout: post
tags:
  - WordPress
  - WP CLI
--- 

In the world of WordPress development, database maintenance is a vital task. Over time, databases can become cluttered with unnecessary entries, affecting both performance and efficiency. This post serves as a guide to harnessing the power of WP CLI commands for bulk deletion, streamlining our WordPress database and keeping the website running at its best.

**1. Purging Spam & Trashed Comments:**

Leverage WP CLI to rid your database of these unnecessary comments. Use the command:

```shell
wp comment delete $(wp comment list --status=spam --format=ids)
wp comment delete $(wp comment list --status=trash --format=ids)
```

**2. Managing Pending Comments:**

Approve valid comments, and clear out the rest with this command:

```shell
wp comment delete $(wp comment list --status=hold --format=ids)
```

**3. Streamlining Post Revisions:**

Optimize by eliminating post revisions using:

```shell
wp post delete $(wp post list --post_type='revision' --format=ids) --force
```

**4. Starting Fresh with Posts:**

Begin anew by deleting all existing posts and focusing on quality content:

```shell
wp post delete $(wp post list --format=ids)
```

**5. Clearing Unnecessary Attachments:**

Improve performance by eliminating unused images and attachments:

```shell
wp post delete --force --allow-root $(wp post list --post_type='attachment' --format=ids --allow-root)
```

**6. Deleting Post Meta by Specific Key:**

Optimize your database by removing post meta with a specific key:

```shell
wp db query "DELETE FROM wp_postmeta WHERE meta_key = 'mashsb_jsonshares'"
```

As a developer, these commands are the easiest items in my performance optimization toolkit. Regular maintenance and focusing on database efficiency will lead to faster, more reliable WordPress.
