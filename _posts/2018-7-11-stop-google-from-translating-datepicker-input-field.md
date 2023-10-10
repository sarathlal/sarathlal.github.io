---
title: Stop Google from translating datepicker input field
layout: post
tags:

---

If we translate form with datepicker using Google translate, the field may show `NaN/NaN/NaN` instead of selected date after compleeting translation.

The Google have solution for it. We need to add `notranslate` to the field or its parent element. Google translate never consider content within this classs for translation.

	<input type="text" class="datepicker notranslate">

If we are using jQuery & jQuery UI datepicker, we can also add class using jQuery during initialization of datepicker.

	$(function() {
        $(".datepicker").datepicker();
        $('.ui-datepicker').addClass('notranslate');
    });
