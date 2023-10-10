---
title: 'Hide Paypal Logo from sidebar &#8211; Magento 1'
author: sarathlal
layout: post
tags:
  - Magento 1
---
In default, Magento themes keep a Paypal logo in right sidebar.

It is little bit tricky to remove this Paypal logo. Actually I can&#8217;t find an option to remove that logo from admin end.

So instead of editing code in template files, I just wish to hide that div using CSS.

In Magento, we have an option to add script from back-end. So lets move in to **System** >> **Configuration **>> **General** >> **Design**.

In **HTML Head **section in Design tab, we have a field to add scripts and styles as Miscellaneous Scripts. So I add my CSS code at there.

<pre>&lt;style&gt;div.paypal-logo, .sidebar .paypal-logo { display : none; } &lt;/style&gt;</pre>

Again reloaded my page & now the Paypal logo is disappeared from my sidebar!
