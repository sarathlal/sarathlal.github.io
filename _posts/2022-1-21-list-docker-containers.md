---
title: List Docker Containers
layout: post
tags:
  - Docker
  - Bash
---

Few commands to list docker containers are listed below.

### Show all running containers

	docker container ls

### Show all containers

	docker container ls -a

###	Show all stopped containers

	docker container ls -f "status=exited"

### Show only container id

	docker container ls -q

###	Show latest created container

	docker container ls -l
	
### Show containers associated with an image

	docker container ls -a --filter "ancestor=image_name"
	
## How to Stop All Docker Containers?

To gracefully terminate all running Docker containers, we can simply use the following command.

	docker stop $(docker container ls -q)
