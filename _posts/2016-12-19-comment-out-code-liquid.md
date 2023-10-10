---
title:  Comment out code in Liquid Template Language
layout: post
tags:
  - Liquid
---

The Liquid is an open-source template language created by Shopify and written in Ruby. It is used in too many projects like Jekyll, Shopify themes etc.

I'm using Liquid for some personal projects and often I have to comment out code in my files.

To comment out code in Liquid, we have to use a special tag.

	{{ "{%" }} comment %}
	this content is comment out
	{{ "{%" }} endcomment %}
