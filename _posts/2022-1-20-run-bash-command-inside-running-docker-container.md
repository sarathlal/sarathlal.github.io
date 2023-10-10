---
title: Run bash command inside a running docker container
layout: post
tags:
  - Docker
  - Bash
---

I need to run some bash commands inside my running Docker container. The 2 solutions are given below.

### 1) Run command from the actual terminal

	sudo docker exec -i <container_id> echo "hello"

### 2) Run command inside pseudo terminal

	docker exec -it <container_id> bash

Now we are inside our container with pseudo terminal. We can use bash command in this pseudo terminal.

	echo "Hello"
