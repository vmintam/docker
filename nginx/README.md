## Nginx Dockerfile


This repository contains **Dockerfile** of [Nginx](http://nginx.org/) for [Docker](https://www.docker.com/)'s [automated build](https://registry.hub.docker.com/u/vmintam/nginx/) published to the public [Docker Hub Registry](https://registry.hub.docker.com/).


### Base Docker Image

* [debian:wheezy]


### Installation

1. Install [Docker](https://www.docker.com/).

2. Download [automated build](https://registry.hub.docker.com/u/vmintam/nginx/) from public [Docker Hub Registry](https://registry.hub.docker.com/): `docker pull dockerfile/nginx`

   (alternatively, you can build an image from Dockerfile: `docker build -t="vmintam/nginx" github.com/vmintam/nginx`)


### Usage

    docker run -d -p 80:80 vmintam/nginx

#### Attach persistent/shared directories

    docker run -d -p 80:80 -v <conf.d-dir>:/etc/nginx/conf.d -v <sites-enabled-dir>:/etc/nginx/sites -v <certs-dir>:/etc/nginx/certs -v <log-dir>:/var/log/nginx vmintam/nginx

After few seconds, open `http://<host>` to see the welcome page.
