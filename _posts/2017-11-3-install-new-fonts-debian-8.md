---
title:  Install new fonts - Debian 8
layout: post
---

	cd Downloads/newfonts
	mv *.ttf /usr/share/fonts/truetype
	cd /usr/share/fonts/truetype
	mkfontscale
	mkfontdir
	fc-cache
	xset fp rehash
