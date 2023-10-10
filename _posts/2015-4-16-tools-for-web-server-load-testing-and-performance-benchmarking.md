---
title: Tools for web server load testing and performance benchmarking
layout: post
tags:
  - Page Optimization
  - Server Optimization
  - Developer tools
---

When making web applications that utilize more server resources, we want to optimize our web pages and hosting servers as much as possible. So understanding the performance of our web pages on servers will help us to take the proper optimization tweaks on both pages and servers.

We already know that almost web servers ( even cheap shared hosting ) can provide an average performance on low traffic. But when we have more traffic, these servers will fail to serve our pages for all visitors.

That means, the performance and scalability testing have an important role in web applications. Now we are going to familiarize three simple but efficient command line tools for load test.

## httperf

#### Installation on Ubuntu & variants

	sudo apt-get install httperf

#### Example

	httperf --server yourdomain.com --port 80 --num-conns 10 --rate 1

1. `server` :- Specifies the IP hostname of the server. By default, the hostname “localhost” is used.
2. `port` :- This option specifies the port number on which the web server is listening for HTTP requests. By default, httperf uses port number 80.
3. `num-conns` :- This specifies the total number of connections to create.
4. `rate` :- Specifies the fixed rate at which connections or sessions are created.

In our exemple, it’s running 10 connections and rate of 1 connection per second.

[More details](http://www.hpl.hp.com/research/linux/httperf/)

## ApacheBench (ab)

ApacheBench (ab) is a single-threaded command line tool to measure the performance of HTTP web servers. Originally designed for the Apache HTTP Server & it is generic enough to test any web server.

#### Installation on Ubuntu & variants

	apt-get install apache2-utils

#### Example 1

	ab -n 1000 -c 5 yourdomain.com

1. `n` :- The number of requests to perform for the benchmarking session. The default is 1 to just perform a single request which usually leads to non-representative benchmarking results.
2. `c` :-  Number of multiple requests to perform at a time. Default is one request at a time.

In this example, it’s sending 1000 number of 5 concurrency requests.

#### Example 2

	ab -kc 20 -t 30 yourdomain.com

The above example open 20 connections and keep alive the connections sending requests to the Web server for 30 seconds.

[More details](http://httpd.apache.org/docs/2.2/programs/ab.html)

## Siege

Siege is a multi-threaded http load testing and benchmarking utility.

#### Installation on Ubuntu & variants

	apt-get install siege

#### Example

	siege -b -c 100 -r 10 yourdomain.com

Running with 100 concurrent connections to the website, running the test in a loop 10 times.

[More details](http://www.joedog.org/siege-manual/)

### Notes

1. Be careful using load test tools against production sites if there resource are too limited. We are making high traffic for small duration. May this will cause for an account suspension or a temporary down state in your server.
2. We want to realize that all of these tools have limitations and they are not 100% accurate. So use all of them to get an abstract & then utilise all possible options to optimize servers and web pages.
