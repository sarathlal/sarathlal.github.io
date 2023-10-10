---
title: All about the !important CSS declaration
author: sarathlal
layout: post
tags:
  - CSS
---

The `!important` CSS declaration is a way to override the usual styles (or Cascaded styles) of web pages by adding a `!important` with the style declaration.

	<p id="thing">I love Green.</p>

	p {
		color: green;
	}
	#thing {
		color: red;
	}

We already know that ID selectors are used for unique HTML elements and they have higher specificity. So our result paragraph will be in red color like below.

<p style="color: red">I love Green</p>

But I like green color for my paragraph. So I want to override this cascaded style to make my paragraph as green. So I use a `!important` with that style declaration.

	p {
		color: green !important;
	}
	#thing {
		color: red;
	}  

Now the paragraph will be in green color by adding more weight on it using `!important`.

<p style="color: green">I love Green</p>

##  What is wrong with !important?

In general, every one like to use `!important` as soon as possible. When some of us feel hardness in modifying styles, we just use `!important` with our styles and works to be done. Some of us have a lazy mindset and we don't like to debug.

But after reading some articles about the subject, I find a funny comparison about `!important` usage. They said that using `!important` is like making nuclear bombs to protect our chickens from fox!

When we use `!important`, we are disrupting the natural flow of our rules, giving more weight to rules that are undeserving of such weight.

The style declaration with `!important` have the highest priority and it make further development as terrible and nightmare. So the usage of `!important` in author style sheet is considered as unmaintainable CSS coding.

If we never use `!important` in our style sheet, then that’s a sign that we well understand CSS and we give proper forethought to our code before writing it.

So we must try to avoid the use of `!important` in author style sheet.

##  So where I can use !important?

The `!important` is still exist in even CSS3 and everyone advice to avoid it. So what is the role of `!important` in style sheet?

1.  The User style sheets
2.  The utility classes like button, clearfix etc
3.  Temporarily Fix an Urgent Problem
4.  For Print Style sheets
5.  To Override Inline Styles in User Generated Content

Surely, we can find good areas to use `!important` in our style sheet like above lists. But use it with care, it is a nuclear bomb and never use it towards fox to keep away them from our chickens!
