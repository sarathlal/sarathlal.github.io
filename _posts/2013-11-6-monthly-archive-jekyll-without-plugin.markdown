---
layout: post
title: Make an Archive page for Jekyll without plugins
tags:
- Jekyll

---

The archive pages are essential for blogs & CMS. The Jekyll haven't any default way to generate archive pages. We want to use plugins to easily generate them.

But in Jekyll, we can get whole posts in reverse chronological order through `site.posts`. With some additional liquid markup, we can make it as a month based archive page.

	{% raw %}
	<h1 class="archive-header">Blog Archive</h1>
	{% for post in site.posts %}
	  {% capture month %}{{ post.date | date: '%m%Y' }}{% endcapture %}
	  {% capture nmonth %}{{ post.next.date | date: '%m%Y' }}{% endcapture %}
	    {% if month != nmonth %}
	      {% if forloop.index != 1 %}</ul>{% endif %}
	      <h3 class="sub-header">{{ post.date | date: '%B %Y' }}</h3><ul>
	    {% endif %}
	  <li><span class="time">{{ post.date | date: "%d/%m/%Y" }}</span><a href="{{ post.url }}">{{ post.title }}</a></li>
	{% endfor %}{% endraw %}

The `{{ "{%" }} capture %}` tag used in this code help us to get the month and year of posts. First we capture latest post's month & year and the one that follows it.

Then we compare them and if they're different, the month and year inserted before a link to the post while if they're the same, the post is simply added to the list for that month.

This process is repeating till the end by picking each post's month & year and the one that follows it.

All credits are going to [Mr. Zak][1] for this awesome code snippet.

If you like a year based archive pages, just play with this code snippets. It is easier than you think.

 [1]: http://www.mitsake.net/2012/04/archives-in-jekyll/ "Mr. Zak post about month based archive for Jekyll"


