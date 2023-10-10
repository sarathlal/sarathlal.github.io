---
title:  Download webpage for offline reading - wget
layout: post
tags:
  - Linux
  - Linux Commands
---

During web browsing, often I feel that I have to save that web pages for further reading. In such situations, always I bookmark URL & later return to that web page in my free time.

But recently, I got enough free time. But there is no internet access! So I need to find out a way to download website completely for offline reading. 

There is too many tools like [HTTrack](https://www.httrack.com/){:target="_blank"}. Also we can use default `wget` command.

	wget --mirror --convert-links --adjust-extension --page-requisites --no-parent http://example.org

The above command will download example.org webpage & and convert all links to access offline.

We can also shorten the above command.

	wget -mkEpnp http://example.org

Explanation of the various flags that used in this command is given below.

1. `--mirror` – Makes (among other things) the download recursive.
2. `--convert-links` – convert all the links (also to stuff like CSS stylesheets) to relative, so it will be suitable for offline viewing.
3. `--adjust-extension` – Adds suitable extensions to filenames (html or css) depending on their content-type.
4. `--page-requisites` – Download things like CSS style-sheets and images required to properly display the page offline.
5. `--no-parent` – When recursing do not ascend to the parent directory. It useful for restricting the download to only a portion of the site.
