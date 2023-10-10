---
title: Sort elements in a list - Python
layout: post
tags:
  - Python
---

#### Sort list item as per the order in another list

I need to sort elements in `a` as per the order in `b`.

	a = ['S', 'XXL', 'M', 'L' ]
	b = ['XS','S','M','L','XL','XXL']
	a.sort(key=lambda (x): b.index(x))
	print a
	>>>['S', 'M', 'L', 'XXL']

#### Sort in asending order

	K = ['22', '40', '70', '10']
	K = sorted(K)
	print K
	>>>['10', '22', '40', '70']

#### Sort in desending order

	K = ['22', '40', '70', '10']
	K = sorted(K, reverse=True)
	print K
	>>>['70', '40', '22', '10']

