---
title: Installing Docker on Linux Mint 20.x / Ubuntu (Jammy 22.04 / Impish 21.10 / Focal 20.04 / Bionic 18.04)
layout: post
tags:
  - Docker
  - Ubuntu
  - Mint
---

## Uninstall old versions

    sudo apt-get remove docker docker-engine docker.io containerd runc

If `apt-get` reports that none of these packages are installed, that means we havn't installed Docker previously.

## Installation

I prefer setting up Docker’s repository and install from that source for ease of installation and upgrade.

### Set up the repository

1. Update the apt package index


		sudo apt-get update

2. Install required packages


		sudo apt-get install ca-certificates curl gnupg lsb-release

3. Add Docker’s official GPG key


		sudo mkdir -p /etc/apt/keyrings
		curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /etc/apt/keyrings/docker.gpg

4. Set up the repository

#### Linux Mint 20.x

The Linux Mint 20.x is based on Ubuntu focal & we have to use it as source.

    echo "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.gpg] https://download.docker.com/linux/ubuntu focal stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null

#### Ubuntu  - Jammy 22.04 / Impish 21.10 / Focal 20.04 / Bionic 18.04

    echo "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.gpg] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null


### Install Docker Engine

1. Update the apt package index

		sudo apt-get update

2. Install the latest version of Docker Engine, containerd, and Docker Compose.

		sudo apt-get install docker-ce docker-ce-cli containerd.io docker-compose-plugin
