---
title: Installing Docker Compose in Linux Mint 20
layout: post
tags:
  - Docker
--- 

### Install required packages & tools

	sudo apt update
	sudo apt install wget curl

### Download docker compose

	curl -s https://api.github.com/repos/docker/compose/releases/latest | grep browser_download_url  | grep docker-compose-linux-x86_64 | cut -d '"' -f 4 | wget -qi -

### Make the script executable

	chmod +x docker-compose-linux-x86_64

### Move the file inside PATH directory

	sudo mv docker-compose-linux-x86_64 /usr/local/bin/docker-compose

### Verify that installation was successful

	docker-compose version
