# docker-node-edge-opencv 
[![docker pulls](https://img.shields.io/docker/pulls/aurlaw/node-edge-opencv.svg)](https://registry.hub.docker.com/u/aurlaw/node-edge-opencv/) [![image size](https://img.shields.io/imagelayers/image-size/aurlaw/node-edge-opencv/latest.svg)](https://imagelayers.io/?images=aurlaw%2Fnode-edge-opencv:latest)



Docker image for NodeJS with [OpenCV](http://opencv.org/) with support for [EdgeJS](https://github.com/tjanczuk/edge)

## Quickstart

- In your shell:

```sh
docker pull aurlaw/node-edge-opencv:2.4.12
docker run --name test_opencv -it aurlaw/node-edge-opencv:2.4.12 /bin/bash
```

- In your `Dockerfile`:

```
FROM aurlaw/node-edge-opencv:2.4.12
```


### Usage with `docker-compose`

```yaml
# https://docs.docker.com/compose/yml/

version: '2'
services:
  backend:
    image: aurlaw/node-edge-opencv:2.4.12
    container_name: test_opencv
    command: "node lib"
    # command: "/usr/local/bin/npm install --verbose"
    working_dir: /srv/node
    environment:
      - LD_LIBRARY_PATH=$LD_LIBRARY_PATH:/usr/local/opencv/build/libdocke
      - NODE_ENV=production
    expose:
      - "3000"
    volumes:
      - .:/srv/node
      - /usr/lib/beignet:/usr/lib/beignet:ro
    devices:
      - "/dev/video0:/dev/video0"
      - "/dev/dri/card0:/dev/dri/card0"
```

```sh
docker-compose up -d
```


### Latest tagged releases

You can find the latest available tags at [hub.docker.com](https://hub.docker.com/r/aurlaw/node-opencv/tags/)

- `aurlaw/node-edge-opencv:2.4.12`


## Links

- http://askubuntu.com/questions/412009/open-cl-in-intel
