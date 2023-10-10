---
title: Sarathlal N - Python, PHP, Javascript, Bash, Linux, Docker, CI/CD, Automation, Unit testing, WordPress, WooCommerce
layout: default
description: My name is Sarathlal N and this is my personal blog. I like to write short notes, code snippets & random thoughts here. WordPress, Magento Development & Server Tips.
sitemap:
  priority: 1
  changefreq: 'daily'
---

{% assign post = site.posts.first %}
{% assign content = post.content %}

<h1>
{% if post.title %}
    {{ post.title }}
{% endif %}
</h1>
{{ content }}

----

<h3>Recent posts</h3>
<ol>
  {% for post in site.posts limit:5 %}
    <li><a href="{{ site.url }}{{ post.url | prepend: site.baseurl }}">{{ post.title }}</a></li>
  {% endfor %}
</ol>
----

<h3>Your Questions / Comments</h3>
<p class="after-post">If you found this article interesting, found errors, or just want to discuss about them, please <a href="{{site.baseurl}}/about/">get in touch</a>.</p>
