---
title: Add custom PHP code in Magento 1 CMS page
author: sarathlal
layout: post
tags:
  - Magento 1
---
In Magento, we can't directly add our custom PHP code in CMS page. But we have an option to call our template files as blocks in CMS page.

So if we want to use custom PHP code in Magento CMS page,

1.  first make a new template file (**.phtml file**) with our custom PHP code inside template folder.
2.  Then call it as a block in CMS page like below code snippet.


	    {% raw %}
	    {{block type="core/template" template="page/myfile.phtml"}}
	    {% endraw %}

We can put our file in any where inside template or we can make new folder for this custom files. But when call as block, point to correct file path.

I made my new file inside page folder in template. So when call block, I point to my file inside page folder like **page/myfile.phtml** as template.
