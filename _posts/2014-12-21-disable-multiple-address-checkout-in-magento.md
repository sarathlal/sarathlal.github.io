---
title: 'Disable multiple address checkout in Magento 1'
author: sarathlal
layout: post
tags:
  - Magento 1
---
We can easily disable multiple address checkout option in Magento.

<ol style="color: #535353;">
  <li>
    Login to our Magento Admin Panel
  </li>
  <li>
    Go to <b>System </b> >> <b>Configuration</b>
  </li>
  <li>
    Go to <b>Shipping Settings</b> on the left menu under <b>Sales </b>section
  </li>
  <li>
    Set &#8220;<b>Allow Shipping to multiple addresses</b>&#8221; as &#8220;<strong>No</strong>&#8220;
  </li>
  <li>
    Then Save Configuration
  </li>
</ol>

After finishing all these steps, just flush the Magento cache & reload our page. That is enough.

This is a global setting in Magento. So this setting is not visible while browsing on store level. That means, the section System > Configuration > Sales > Shipping Settings is just visible if your level setting (on the upper left side of the configuration page ) is set to Default Config.
