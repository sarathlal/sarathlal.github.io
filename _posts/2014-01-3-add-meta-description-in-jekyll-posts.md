---
title: Add meta description in Jekyll posts
author: sarathlal
layout: post
tags:
  - Jekyll
---

The meta descriptions in web pages help us to get more visitors through Search Engine Result Pages. They can provide a brief introduction about our content as a search description. But we need unique meta descriptions for our web pages.

In Jekyll, we can use YAML front matter block of posts for this purpose. In our YAML front matter, set up a variable and assign value for that variable. We can access the value of this variable through our site using Liquid tags.

Then we will convert the value of this variable as a content of meta Description tag for our web pages. So remember that the value, the meta description must be a unique tiny description about our content.

If possible, try to use our keywords in meta description & limit meta description length in 160 characters.

**Step 1**: Add meta description in post / page YAML front matter like below example.

    ---
    layout: post
    title: Add meta description in Jekyll posts & get more visitors
    description: We can easily add meta description in Jekyll post. It can generate more visitors for our blog through SERP(Search Engine Result Pages) & indirectly improve SEO.
    ---

**Step 2**: Access this variable from YAML front matter & use it for HTML meta description tag in HTML head section of template file.

	{% raw %}{% if page.description %}<meta name="description" content="{{ page.description }}">{% endif %}{% endraw %}

This line of code say that, if there is any `description` in YAML front matter, use it as a content for HTML meta description tag. If there is no any description at there, Jekyll never generate meta description tag for our web pages.
