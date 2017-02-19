# docker-wordpress-nginx

A Dockerfile that redirects all requests over to HTTPS.

## Installation

The easiest way to get this docker image installed is to pull the latest version
from the Docker registry:

```bash
$ docker pull stormerider/docker-sslify
```

If you'd like to build the image yourself then:

```bash
$ git clone https://github.com/stormerider/docker-sslify.git
$ cd docker-sslify
$ sudo docker build -t="stormerider/docker-sslify" .
```

## Usage

This is intended for use under Rancher. You can use a docker-compose file like so:

```yaml
version: '2'
services:
  wp:
    image: stormerider/docker-sslify
    ports:
    - 80:80/tcp
    command:
    - /bin/bash
    - /start.sh
    labels:
      io.rancher.container.pull_image: always
```

Add that as a new service, or write it to docker-compose.yaml and use docker-compose like so:

```bash
$ sudo docker-compose up -d
```

After starting docker-sslify check to see if it started and the port mapping is correct.  This will also report the port mapping between the docker container and the host machine.

```
$ sudo docker ps

0.0.0.0:80 -> 80/tcp docker-sslify
```

You can the visit the following URL in a browser on your host machine to get started:

```
http://127.0.0.1:80
```
