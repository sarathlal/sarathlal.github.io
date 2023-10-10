---
title: The Markdown markup language, syntax and examples
author: sarathlal
layout: post
tags:
  - Markdown
---
The Markdown is a markup language like HTML, but easy-to-read, easy-to-write plain text format and can be considerable as a minimal alternative to HTML.

But never consider Markdown is an alternative to HTML programming. The Markdown is an alternative to HTML formatting. It is a tool for creating web documents. It simplifies HTML tags that can be usable to format a document.

The philosophy behind Markdown is to produce web based content, which can be &#8220;published as-is, without looking like it&#8217;s been marked up with tags&#8221;. The Markdown is simple and you just need a plain text editor to type your content.

Before learning any languages, we want to understand its syntaxes. Through this post, I like to summarize what I learn from Markdown markup language with examples.

* * *

##  paragraph

A paragraph in Markdown is simply one or more consecutive lines of text, separated by one or more blank lines.

**Markdown example**

	Lorem ipsum dolor sit amet, no nusquam noluisse invidunt pro.
	==========Make this line as blank==========
	Cum ut quidam scribentur, et audiam rationibus eum. Lorem tantas gubergren ut nec, his graeci iisque ea.

**HTML output**

	<p>Lorem ipsum dolor sit amet, no nusquam noluisse invidunt pro.</p>
	<p>Cum ut quidam scribentur, et audiam rationibus eum. Lorem tantas gubergren ut nec, his graeci iisque ea.</p>

* * *

##  Headers

The Markdown support two styles of header.

1.  Atx
2.  Setext

##  Atx style Headers

Atx style headers use 1 to 6 hash `#` characters at the start of the line, corresponding to header levels 1-6.

**Markdown example**

	#Heading one
	## Heading two
	### Heading three
	#### Heading four
	##### Heading five
	##### #Heading six

**HTML output**

	<h1>Heading one</h1>
	<h2>Heading two</h2>
	<h3>Heading three</h3>
	<h4>Heading four</h4>
	<h5>Heading five</h5>
	<h6>Heading six</h6>

##  Setext style headers

Setext-style headers are using underlined equal signs `=` (for first-level headers) and underlined dashes `-` (for second-level headers).

**Markdown example**

	Heading one
	===========

	Heading two
	-----------


**HTML output**

	<h1>Heading one</h1>

	<h2>Heading two</h2>

* * *

##  Block quotes

Markdown uses `>` character for block quoting. We want to use `>` character before paragraph in a block quote.

**Markdown example**

	>    Esse euismod feugait id cum, mel ipsum consequuntur et. An meis utroque inimicus nam, saepe fierent complectitur eu vis. Id docendi suavitate us, vis stet illum impetus no. No vel moderatius reprehendunt, mucius tibique mei at.


**HTML output**

	<blockquote>
	<p>Esse euismod feugait id cum, mel ipsum consequuntur et.
	An meis utroque inimicus nam, saepe fierent complectitur eu vis.
	Id docendi suavitate us, vis stet illum impetus no.
	No vel moderatius reprehendunt, mucius tibique mei at.</p>
	</blockquote>

* * *

##  Ordered list

In Markdown, Ordered lists can be formated via numbers followed by a dot and then a period.

**Markdown Example**

	1. List item 1
	2. List item 2
	3. List item 3
	4. List item 4


**HTML output**

	<ol>
	<li>List item 1</li>
	<li>List item 2</li>
	<li>List item 3</li>
	<li>List item 4</li>
	</ol>

If you want to create a nested list, apply a tab or minimum 4 spaces before the next level list entries.

**Markdown Example**

	1. List item 1
	2. List item 2
		1. List item 2.1
		2. List item 2.2

**HTML output**

	<ol>
	<li>List item 1</li>
	<li>List item 2<ol>
		 <li>List item 2.1</li>
		 <li>List item 2.2</li></ol>
	</li>
	</ol>

* * *

##  Unordered lists

In Markdown, Unordered lists can be formated via either asterisks(*), pluses(+), and hyphens(-) followed by a period.

**Markdown example**

	* List item 1
	* List item 2
	* List item 3
	* List item 4

**HTML output**

	<ul>
	<li>List item 1</li>
	<li>List item 2</li>
	<li>List item 3</li>
	<li>List item 4</li>
	</ul>

* * *

##  Code blocks

The Markdown support pre-formatted code blocks in posts. To make a code block, indent every line of the code by at least 4 spaces or 1 tab.

**Markdown example**

	This is a normal paragraph
		This is the first line of code block
		This is the second line of code block

**HTML output**

	<p>This is a normal paragraph</p>
	<pre>This is the first line of code block
	This is the second line of code block</pre>

* * *

##  Horizontal lines

The Markdown can produce a horizontal rule tag `(<hr />)` by placing three or more hyphens, asterisks, or underscores on a line by themselves. We can add space in between them.

**Markdown example**

	--------
	********
	_______
	_ _ _ _ _
	* * * * *

**HTML output**

	<hr>
	<hr>
	<hr>
	<hr>
	<hr>

##  Links

Markdown supports two style of links.

1.  Inline links
2.  Reference links

##  Inline links

**Markdown example**

	This is the [home page](http://sarathlal.com/ "alt text of home") of my blog.

**HTML output**

	<p>This is the <a href="http://sarathlal.com/" title="alt text of home">home page</a> of my blog.</p>

##  Reference links

**Markdown example**

	This is the [Home page][1] of my blog. Some lorem ipsum comes here as a paragraph.

	[1]: http://sarathlal.com (alt title for my blog)


Note: In the above Markdown example, the first sentence is the Markdown formatting and second line is the link definition. We can define the link any where in our documents. Link definitions are only used for creating links during Markdown processing, and are stripped from our document in the HTML output.

**HTML output**

	<p>This is the <a href="http://sarathlal.com/" title="alt text of home">home page</a> of my blog.</p>

* * *

##  Bold and Italics

Instead of `<b>` and `<i>`, markdown use `<strong>` and `<em>` tags. They are similar in nature and more SEO friendly.

Markdown consider single asterisks `(*)` and single underscores `(_)` as indicators of emphasis. Just wrap our text with it and Markdown will convert it in to emphasis characters.

Also double asterisks `(**)` and double underscores `(__)` as indicators of emphasis. Just wrap our text with it and Markdown will convert it in to strong characters.

**Markdown Example**

	*This is a italic*
	_This is also italic_
	**This is bold**
	__This is also Bold__

**HTML output**

	<em>This is a italic</em>
	<em>This is also italic</em>
	<strong>This is bold</strong>
	<strong>This is also Bold</strong>

* * *

##  Code

To indicate a span of code, we want to wrap it with backtick quotes (\`). A code span means code within a paragraph.

**Markdown Example**

	Use `printf()` function to output some thing.

**HTML output**

	Use <code>printf()</code> function to output some thing.

* * *

##  Images

We know that adding image tag in a HTMl document using a plain text editor is enough difficult for bloggers. But in the Markdown, there is also some syntax to add images in our posts.

Same like links, the Markdown support two style syntax to place an image.

1.  Inline image links
2.  Reference image links.

The inline image link syntax is almost same like internal links.

	![Alt text for image](/path/to/img.jpg)
	or
	![Alt text for image](/path/to/img.jpg "Optional title")

The reference image link syntax is given below.

	![Alt text for image][id]

	[id]: url/to/image  "Optional title attribute"

Same like the reference links, the first line is the image formatting and second line is the image definition in Markdown. We can put image definition in any where in our post and it is stripped from HTML output.

But the Markdown has no syntax for specifying the dimensions of an image; if this is important to us, we want to use regular HTML `<img>` tags.

* * *

##  Automatic links

The markdown support a shortcut style for creating &ldquo;automatic&rdquo; links for URLs and email addresses. If we wrap the URL or email address with angle brackets, markdown consider it as a link.

**Markdown example**

	<http://twitter.com>

**HTML output**

	<a href="http://twitter.com">http://twitter.com</a>

* * *

##  Backslash Escapes

Markdown allows us to use backslash escapes to generate literal characters which would otherwise have special meaning in Markdown&rsquo;s formatting syntax.

Markdown provides backslash escapes for the following characters.

	\   backslash
	`   backtick
	*   asterisk
	_   underscore
	{}  curly braces
	[]  square brackets
	()  parentheses
	#   hash mark
	+   plus sign
	-   minus sign (hyphen)
	.   dot
	!   exclamation mark

If we want to use any of these characters in our post, just add a backslash (``) before it.

**Markdown example**

	\*This is italic\*

**HTML output**

	*This is italic*

We already discuss about italic and bold formatting in Markdown. But in this example, I use a backslash before asterisks. So this asterisks are escaped from Markdown formatting.

* * *

##  Special characters

If we want to use any special characters like `>`,`>`,`&` etc, we want to escape it from Markdown formatting.

That means, If we want to use them as literal characters, we must escape them as entities like `&lt;`, and `&amp;` etc.

* * *

##  conclusion

I tried to collect almost Markdown examples at here. Same like other posts in this blog, this post is also a exercise for me to learn the Markdown. So if you feel any doubt or confusion, just google about it.
