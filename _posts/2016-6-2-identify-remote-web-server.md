---
title: Identify remote web server
layout: post
tags:
  - Linux
  - Server
  - Linux Commands
---

When hosting applications, often I want to get the details of remote servers.

We can easily find out essential detail of server with a single command.

Use `curl` command with the `-I` option to make a HEAD request and see the HTTP headers.

	curl -I http://example.com

The result will look like below one.

	HTTP/1.1 200 OK
	Content-type: text/html
	Content-Length: 0
	Date: Mon, 28 Jan 2008 08:53:54 GMT
	Server: lighttpd

Note : You have to install curl before using curl commands.
