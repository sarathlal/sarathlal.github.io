---
layout: post
title: Escape Liquid template tags in Jekyll posts
tags:
- Jekyll
---

Have you ever tried to add some Liquid tags in your Jekyll powered blog posts as a code snippet? The Jekyll normally interpreting Liquid tags in posts even if they are in code block.

After some searches, I find two simple methode to escape Liquid tags in Jekyll posts. I tried both and they both works on my blog including this post. 

### Solution 1
if we wrap any thing in posts with `{{ "{%" }} raw %}` and `{{ "{%" }} endraw %}` tags, they will escape from formatting in Jekyll.

If we want to display a liquid tag as a word in paragraph, we want to wrap our liquid tag with `{{ "{%" }} raw %}` and `{{ "{%" }} endraw %}` tags.

For example, the markdown {{ "{%" }} raw %}{{ "{{" }} page.date }}{{ "{%" }} endraw %} is converted in to {% raw %}{{ page.date }}{% endraw %} in HTML output.

If we want to display a liquid tag as a span of code in paragraph, additionally we want to wrap our liquid tag with backtick quotes (\`).

Consider the same example, the markdown {{ "{%" }} raw %}\`{{ "{{" }} page.date }}\`{{ "{%" }} endraw %} is converted in to {% raw %}`{{ page.date }}`{% endraw %} in HTML.

We can use this same escaping method for Liquid tags in code blocks. But if our code block have any other language tags (especially HTML), we want to use syntax highlighting for that language tags with {% raw %} and {% endraw %} tags like below example.

    {{ "{%" }} highlight html %}{{ "{%" }} raw %}
    \\our code block with Liquid & HTML tags comes here
    {{ "{%" }} endraw %}{{ "{%" }} endhighlight %}

### Solution 2

I also find a [stack overflow answer](http://stackoverflow.com/questions/3426182/how-to-escape-liquid-template-tags "Escape Liquid template tag Jekyll - stack overflow answer") about this issue. It use a different method by escaping characters of liquid markup.

Let's say we want to display `{{ "{%" }} hello %}`, then we want to type `{{ "{{" }} {{ '"{%"' }} }} hello %}` and if we want to display `{{ "{{" }} hello }}`, then we want to type `{{ "{{" }} {{ '"{{"' }} }} hello }}`.

Next time, when you want to display code snippet with Liquid tag in your Jekyll blog, use this tips and make beautiful code snippets in your Jekyll blog.
