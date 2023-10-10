---
title:  Call static block in layout file, phtml file or CMS content - Magento 2
layout: post
tags:
  - Magento 2
---


#### In Layout file

	<block class="Magento\Cms\Block\Block" name="our_block_name">
	<arguments>
	<argument name="block_id" xsi:type="string">our_block_identifier</argument>
	</arguments>
	</block>

#### In PHTML file

	<?php echo $block->getLayout()->createBlock('Magento\Cms\Block\Block')->setBlockId('our_block_identifier')->toHtml();?>

#### In CMS page content

	{% raw %}
	{{block class="Magento\\Cms\\Block\\Block" block_id="our_block_identifier"}}
	{% endraw %}
