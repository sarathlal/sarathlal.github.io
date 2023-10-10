---
title: Noindex Jekyll posts using meta robot tags
author: sarathlal
layout: post
tags:
  - Jekyll
---
The search engines are great stuffs, they will pick our content and promote them. When we publish new web pages, Search engine automatically pick them with in days and provide search result based on the content.

But in some situations, every one want to hide some of their content in search result. We can use different methods like `meta robot tags` and `robot.txt` file for this purpose.

Usage of page wise meta robot tags is consider as the best option than `robot.txt` file for HTML web pages. So through this post, we try to add some meta robot tags in our Jekyll blog posts & pages to noindex them.

In regular cases, if there is no any meta robot tags in our web pages, search engines automatically index our content like content with `<META NAME="ROBOTS" CONTENT="INDEX,FOLLOW"/>` meta robot tag.

To hide some of my content from search results, I like to add meta robot tag, `<META NAME="ROBOTS" CONTENT="NOINDEX,FOLLOW"/>` only on these web pages and leave other web pages without any meta robot tags.

That means, normally all my web pages are indexed & followed by spiders and my hidden web pages are non indexed but followed by them.

So first we can make some marking on our posts & pages to be noindexed. We can use YAML front matters for this purpose.

*   Add a variable & and its value as `TRUE` to the YAML front-matter on post / page, they don&rsquo;t want to be indexed.

		noindex: true

Then the `head` of this post / page need `<META NAME="ROBOTS" CONTENT="NOINDEX,FOLLOW"/>` meta robot tag.

*   Make an if statement in template `head` section to check the condition of variable in YAML front matter.
*   If the condition is true, we want to add `<META NAME="ROBOTS" CONTENT="NOINDEX,FOLLOW"/>` meta robot tag on `head` section of that post / page.
*   If the condition is falls, nothing to be happened.

So add this if statement in your template `head` section & save file.

	{% raw %}
	{% if page.noindex %}
	<META NAME="ROBOTS" CONTENT="NOINDEX,FOLLOW"/>
	{% endif %}
	{% endraw %}

Can you make a sample post with our new YAML front matter? Then generate your Jekyll site one more time and check the source of some posts to verify our code. You can only find our meta robot tag only on our sample post.
