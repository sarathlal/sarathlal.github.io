---
title: Date formats in Liquid Templating Engine & Jekyll
author: sarathlal
layout: post
tags:
  - Jekyll
  - Liquid Templating Engine
---

The Date is an essential entity for blogs. The blogs are contents arranged in reverse chronological order. If we don't have a published date, there is no blogging at all.

My blog is a Jekyll powered static website and it use Liquid Templating Engine. I like to use dates in different formats at here. After some readings, I collected a list of date formats usable in Liquid for Jekyll & GitHub pages.

The simple Liquid date tag {% raw %}`{{ page.date }}`{% endraw %} can generate published date like `{{ page.date }}`. Are you like this published date for our Jekyll blog post?

Now we can try to change our date format to display more concise one. The {% raw %}`{{ page.date | date_to_string }}`{% endraw %} can generate a neat date like `26 Jan 2014`.

There are some default built-in Liquid date formats to get date in Jekyll pages. Why can't try them?

The {% raw %}`{{ page.date | date: "%c" }}`{% endraw %} can output date like `Sun Jan 26 00:00:00 2014` and the {% raw %}`{{ page.date | date: "%x" }}`{% endraw %} result will be `01/26/14`.

Are you irritated with these examples? I realize that they are enough for certain situations. But if you need more flexibility, we can add some filters and generate new date formats.

Can you try {% raw %}`{{ page.date | date: "%B %d, %Y" }}`{% endraw %}? This will generate date like `January 26, 2014`.

Even if you need the name of the day with your dates like `Sunday - Jan 26, 2014`, insert {% raw %}`{{ page.date | date: "%A - %b %d, %Y" }}`{% endraw %}.

What is your opinion about `26-01-2014` and `26/01/2014`. The {% raw %}`{{ page.date | date: "%d-%m-%Y" }}`{% endraw %} and {% raw %}`{{ page.date | date: "%d/%m/%Y" }}`{% endraw %} can generate them.

The beginning `0` on date and month annoying me. Have you tried {% raw %}`{{ page.date | date: "%B %-d, %Y"}}`{% endraw %} or {% raw %}`{{ page.date | date: "%-d/%-m/%y"}}`{% endraw %}. The result will be omitting `0` from the beginning like `January 26, 2014` and `26/1/14`.

Even if you like to use last two digit of year with your date like `1/26/14`, date tag {% raw %}`{{ page.date | date: "%-m/%-d/%y"}}`{% endraw %} can solve your problem.

Have you get your favorite date format for your Jekyll blog that use Liquid Template engine? Else combine and replace some elements and try yourself.
