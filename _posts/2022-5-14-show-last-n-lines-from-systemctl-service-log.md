---
title: Show the last n lines from systemctl service log - Linux
layout: post
tags:
  - Linux
  - Ubuntu
  - Debian
---

I need to print the last `n` lines from a `systemctl` service log in Linux. The command is given below.

    journalctl -u <service name> -n <number of lines> -f --no-pager

*Example*

    journalctl -u my_service_name.service -n 100 -f --no-pager

