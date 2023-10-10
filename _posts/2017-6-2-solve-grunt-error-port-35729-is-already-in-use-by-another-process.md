---
title: Solve Grunt error - Port 35729 is already in use by another process
layout: post
tags:
  - Grunt
---

#### Find tasks that using port 35729

	sudo lsof | grep 35729

#### Kill the process using process ID

	sudo kill -9 process_id
