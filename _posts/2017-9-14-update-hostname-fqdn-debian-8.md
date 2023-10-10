---
title:  Update hostname and FQDN - Debian 8
layout: post
tags:
  - Managing Server
---

>Your system needs to have a fully qualified domain name (fqdn) in order to ........

If you ever get such an error message from our server, then we need to set a Fully Qualified Domain Name (FQDN) on our Debian server.

To do so, we need to edit the file `/etc/hosts` and `/etc/hostname`.

Let’s assume our desired FQDN is `foobar.example.com`:

* Edit `/etc/hosts` and make sure these two lines are present.

		127.0.0.1	localhost
		127.0.1.1	foobar.example.com foobar


* Edit `/etc/hostname` content as follow:

		foobar


* Update hostname service:

		/etc/init.d/hostname.sh

Now check our updates

	root@server:~# hostname
	foobar.example.com


	root@server:~# hostname --fqdn
	foobar.example.com

	root@server:~# hostname -f
	foobar.example.com


	root@server:~# dnsdomainname
	example.com

Note: FQDN and the hosted domain names don't have any relationship. We can use any domain name as our FQDN. Some random text (xxxx.xxxxx.xxx format) is always better.
