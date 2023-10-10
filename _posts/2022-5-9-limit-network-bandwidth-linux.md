---
title: Limit network bandwidth in Linux
layout: post
tags:
  - Linux
  - Ubuntu
  - Debian
---

Recently, I needed to reduce my network bandwidth in my system to do some automation testing using Selenium. Here is the solution for the purpose.

First we want to know the network interface which we want to limit bandwidth usage. We can use `ifconfig` or `ip addr`.

Here is the output of the `ifconfig` command in my system.

    lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536
            inet 127.0.0.1  netmask 255.0.0.0
            inet6 ::1  prefixlen 128  scopeid 0x10<host>
            loop  txqueuelen 1000  (Local Loopback)
            RX packets 750202  bytes 109236649 (109.2 MB)
            RX errors 0  dropped 0  overruns 0  frame 0
            TX packets 750202  bytes 109236649 (109.2 MB)
            TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

    wlp0s20f3: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
            inet 10.0.0.30  netmask 255.255.255.0  broadcast 10.0.0.255
            inet6 fe80::50ae:c446:f5ba:84d6  prefixlen 64  scopeid 0x20<link>
            ether dc:21:48:b7:da:e5  txqueuelen 1000  (Ethernet)
            RX packets 1907587  bytes 1240898453 (1.2 GB)
            RX errors 0  dropped 143  overruns 0  frame 0
            TX packets 1437275  bytes 654470151 (654.4 MB)
            TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

My active wireless interface is `wlp0s20f3`.

Next install `wondershaper`.

    apt-get install wondershaper

#### Command to limit network bandwidth

    wondershaper [-hcs] [-a <adapter>] [-d <rate>] [-u <rate>]

1. `-h` :  Display help
2. `-a` :  Set the adapter
3. `-d` :  Set maximum download rate (in Kbps) and/or
4. `-u` :  Set maximum upload rate (in Kbps)
5. `-p` :  Use the presets in /etc/systemd/wondershaper.conf
6. `-f` :  Use alternative preset file
7. `-c` :  Clear the limits from adapter
8. `-s` :  Show the current status of adapter

#### Example

    wondershaper -a wlp0s20f3 -d 4048 -u 2024

Now the download rate will be set to `4Mbps` & upload rate will be `2Mbps`.

#### Command to view current status of network adaptor

    wondershaper -sa wlp0s20f3

#### Command to clear the download or upload limits

    wondershaper -ca wlp0s20f3
