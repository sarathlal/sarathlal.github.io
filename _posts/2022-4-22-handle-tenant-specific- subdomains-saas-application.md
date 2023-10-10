---
title: Handle tenant specific subdomains for SaaS application
layout: post
tags:
  - SaaS
---

Consider that we have a cloud SaaS solution and all our customers use our product at https://www.awesomesite.com.

With custom subdomains, Customer A can use the product at https://customerA.awesomesite.com, and similarly, Customer B can use the product at https://customerB.awesomesite.com.

### Pros of this method

1. Subdomains can provide tenants better isolation with better security control for cookies, cross-origin resources sharing, etc.
2. With the help of DNS and Load Balancer configuration, subdomains can help us to configure tenant-specific hardware if required.

It is better to design our application without subdomains by default, and then bake in custom subdomain functionality as an additional feature/layer. If we integrate subdomains all the way through from the beginning, then it might become very inflexible to change it in the future.

Different methods to achieve the requirement given below.

### Using DNS and CNAME

A major drawback of this design is DNS propagation. Every time customers configure a new subdomain, we will add a new CNAME record to the DNS. As DNS propagation is not instantaneous, your customers might have to wait (maybe a few hours) before they can use their newly configured subdomain.

### Using Reverse Proxy Server

In this approach, we have a single wildcard DNS entry (*.awesomesite.com) which points to a reverse proxy server (varnish, haproxy, Nginx, etc.), and keeping the entries for routing subdomain to the actual backend servers in this reverse proxy server.

May a reverse proxy server is a bottleneck and can become a single point of failure. But handling subdomain entries in the reverse proxy is much better than managing them in the DNS.

### Using Servlet Filter

This is known as the best option among these 3 methods. But I didn't try & I'm completely zero in this option. So no comments now.
