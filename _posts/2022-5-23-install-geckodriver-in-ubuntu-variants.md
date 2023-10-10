---
title: Install Geckodriver in Ubuntu & its variants
layout: post
tags:
  - Python
  - Selenium
  - Test Automation
  - Firefox
---

Gecko is a web browser-engine used in many applications developed by Mozilla Foundation and the Mozilla Corporation. Geckodriver is the link / connection between other applications and the Gecko-based browsers.

We can also say that Geckodriver is a proxy for using W3C WebDriver-compatible clients to interact with Gecko-based browsers like Mozilla Firefox etc.

Go to the geckodriver releases page (https://github.com/mozilla/geckodriver/releases). Find the latest version of the driver for your platform and download it. For example:

    wget https://github.com/mozilla/geckodriver/releases/download/v0.31.0/geckodriver-v0.31.0-linux64.tar.gz

Extract the file with tar command:

    tar -xvzf geckodriver*

Make it executable:

    chmod +x geckodriver

Move files to /usr/local/bin/ path to easily access.

    sudo mv geckodriver /usr/local/bin/




