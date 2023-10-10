---
title:  Hide 'Show Toolbar' option in WordPress profile page
layout: post
tags:
  - WordPress
---

![Hide show toolbar option in profile page](/images/2017/hide-show-toolbar-option-profile-page-wordpress.png)

	//Hide 'Show Toolbar' option in WordPress profile page
	function hide_toolbar_option() { ?>
		<style type="text/css">.show-admin-bar { display: none; }</style>
	<?php }
	add_action('admin_print_scripts-profile.php', 'hide_toolbar_option');
