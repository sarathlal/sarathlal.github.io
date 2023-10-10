---
title:  The add_image_size() function - WordPress best practices
layout: post
tags:
  - WordPress
---

Have you ever get a warning or notice from your web host that inform you have exceeded your disk quote? When you backup your simple WordPress site, did you noticed that the compressed file is too large?

In our WordPress projects, I have faced this situation too many times. In almost cases, the resized images are the main cause for this warning and large back up size.

When we upload an image to WordPress, the WordPress generate the file in various image sizes that defined in WordPress settings & our custom functions. That means, in the uploaded directory, we have duplicate of an image in various size. These duplicates can consume a large space in our hosting.

Some times, we never consider / aren't aware the effect of `add_image_size()` function in file size. We just use the function to get resized images.

Even in some projects, we never use default WordPress media settings! If the project is using WooCommerce plugin, there is chance to ignore the WooCommerce settings to resize the product images! Also we add custom image size using the `add_image_size()`.

The result is unnecessary 10 to 12 resized images, low disk space and bulk size on backups.

## The best practices

1. Use default media settings (Settings >> Media) to resize images.
2. Enter 0 as width and 0 as height on unnessory options in media settings. That means, it never generate image on that size.
3. As much as possible, try to use default media size in our theme.
4. If it is too required, only use custom image sizes.
5. If using WooCommerce plugin, use the WooCommerce media settings (WooCommerce >> Settings >> Products >> Display) to resize product images.
6. Resize images using offline tools and upload that one.
