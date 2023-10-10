---
title: Call a template file - Magnto 1
author: sarathlal
layout: post
tags:
  - Magento 1
---
Calling a core template file in .phtml file

    <?php echo $this->getLayout()->createBlock('core/template')->setTemplate('templateFolder/ourfile.phtml')->toHtml(); ?>

Calling a core template file in CMS page

	{% raw %}
    {{block type="ore/template" template="templateFolder/ourfile.phtml"}}
	{% endraw %}
