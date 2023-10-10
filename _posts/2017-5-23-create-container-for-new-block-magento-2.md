---
title:  Create a container for new block - Magento 2
layout: post
tags:
  - Magento 2
---

When adding block in layout file, declare our container before block declaration.

	<container name="some.container" as="someContainer" label="Some Container" htmlTag="div" htmlClass="some-container" />
	...
	Block code comes here
	...
	</container>

The above code will create a `DIV` container for content from block with CSS class `some-container`. The htmlTag will be a div, ul, span etc any HTML element.
