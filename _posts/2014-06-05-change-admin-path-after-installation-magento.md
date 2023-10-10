---
title: Change admin path after installation - Magento 1
author: sarathlal
layout: post
tags:
  - Magento 1
---
Changing admin path name is one of the important security action in Magento E-Commerce stores after installation. During installation period, we have an option to change default admin path `admin` to any another path name.

But we can also rename admin path after installation. To rename admin path, first we want to go to `/app/etc` and then open `local.xml` file.

Find the text `![CDATA[admin]]` in the file. This is the default admin path. Then change admin name to some other name like kap_store etc. 

So it will look like `![CDATA[kap_store]]` and admin url will be `http://www.our-domain.com/kap_store`.
