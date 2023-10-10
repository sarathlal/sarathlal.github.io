---
title: The Amazing Adventure - Solving the Mysteries of a WooCommerce Store
layout: post
tags:
  - WordPress
  - Optimization
  - WordPress Plugins
  - WooCommerce
---

It was a regular week when I started an extraordinary journey. I took on the task of optimizing a WooCommerce store that had a wide range of products and orders. The technical setup seemed impressive—a managed VPS with a powerful 8GB RAM and a spacious 160GB storage.

But, unfortunately, the admin section was incredibly slow. Each click in the admin area would make me wait for a frustrating 20 to 30 seconds, sometimes even up to a minute before my browser gave up and timed out.

However, amidst this slowness, the front end of the store was working fine. Customers were happily buying items without any issues. It was a good sign!

Determined to find out what was causing this strange situation, I began a daring quest. With patience, I painstakingly cloned the entire website to my local machine, which was quite large in size—2GB for the database alone and over 50GB in total. Working on the live site was not an option since customers were actively making purchases, and I couldn't risk downtime or a slow recovery.

Armed with determination, I started optimizing the website. I removed unnecessary data like temporary files, old versions, deleted content, and unused options. I used a tool called WP-CLI, which helped me complete these tasks in just 10 minutes. I also got rid of over a hundred thousand unapproved comments, thanks to WP-CLI once again.

However, the admin side of the store still suffered from slowness. It was time to take drastic measures.

I activated the "Query Monitor" plugin, which showed me some shocking results. A single WordPress admin page triggered a massive number of 65,020 SQL queries, consuming a whopping 1,860MB of data! While "Query Monitor" gave me some insight, when I tried to dig deeper, my page froze, and I couldn't do anything.

![Slow admin pages due to payment gateway plugin - WooCommerce](/images/2023/7/optimizing-woocommerce-store-slow-admin-side-payment-gateway-plugin-surprise.png)

To my astonishment, I made a remarkable discovery. The store was using a custom theme, so I switched to the default theme, thinking it might help. Unfortunately, it didn't change anything.

Undeterred, I decided to systematically disable plugins one by one, starting with the unfamiliar and less popular ones. But even after removing them, the problem persisted. Next, I focused on plugins that handled bulk data. Despite removing them, I still didn't see any improvement.

Finally, I turned my attention to the plugins I trusted, the ones that had never let me down before. And guess what? In the midst of this unfolding drama, when I renamed a payment gateway plugin, the admin pages became lightning-fast, and the number of queries dropped to just 250.

Can you believe it? A payment gateway plugin, designed to handle transactions, was causing a flood of 65,020 SQL queries across all admin pages. It was bewildering and relentless, a testament to the intricate nature of WordPress and PHP.

As software developers, we have the power to code, but true greatness lies in writing good code. We often blame programming languages and frameworks for performance issues, but the real problem often lies in our own code quality. Unit testing, code reviews, and quality assurance can help us identify these issues, but sometimes we still fail.

So, here is the happy ending to our story. Before we start writing code, let's understand its impact and strive for infinite possibilities. Our code is the backbone of many businesses. It builds trust among users and generates income. Therefore, let's commit ourselves to writing high-quality code. And if we can't, maybe it's better not to write a single line of code intended for production.
