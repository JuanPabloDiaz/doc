---
layout: post
title: "Install Docker & Portainer on Raspberry Pi"
date: 2021-10-28
categories: home-lab
tags: home-lab neverstoplearning raspberrypi docker portainer
---

This is one of the easiest way to install docker and Portainer on a Raspberry Pi.

### Update and upgrade your system.

```bash
    Sudo apt-get update && sudo apt-get upgrade
```

### Install **git**

```bash
   Sudo apt install git
```

### Install **Docker**

```bash
    1. Mkdir Downloads
    2. cd Downloads
    3. git clone https://github.com/novaspirit/pi-hosted
    4. cd pi-hosted
    5. ls
    6.   ./install_docker.sh    #install docker
    7. exit   #logout
    8. login
    9. groups  # to check if docker is in the group
```

## Install **Portainer**

```bash
    1. cd Downloads/pi-hosted
    2. ./install_portainer.sh
```

<!-- ACKNOWLEDGMENTS -->

#### Acknowledgments 📚

Resources list that I find helpful and would like to give credit to.

Thanks to [Novaspirit tech](novaspirit.com), I can not only install docker with one script, but also setup my own home server and host plenty of apps. Follow his channel to see more tutorial.

<br>

---

This article is publish in [Dev](https://dev.to/1diazdev/install-docker-on-raspberry-pi-12ph)
