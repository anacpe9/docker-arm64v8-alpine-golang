# Alpine + QEMU + ARM64 (aarch64) + Golang

[![Docker Build Status](https://img.shields.io/docker/build/anacha/arm64v8-alpine-golang.svg)](https://hub.docker.com/r/anacha/arm64v8-alpine-golang)

[![](https://images.microbadger.com/badges/version/anacha/arm64v8-alpine-golang.svg)](https://microbadger.com/images/anacha/arm64v8-alpine-golang "Get your own version badge on microbadger.com")
[![](https://images.microbadger.com/badges/version/anacha/arm64v8-alpine-golang:4.svg)](https://microbadger.com/images/anacha/arm64v8-alpine-golang:1.12 "Get your own version badge on microbadger.com")
[![Layers](https://images.microbadger.com/badges/image/anacha/arm64v8-alpine-golang.svg)](https://microbadger.com/images/anacha/arm64v8-alpine-golang "Get your own image badge on microbadger.com")

This project enables building a *Docker* image to allow running *64-bits ARM*
*Alpine Linux* builds on non-arm hosts (like [Travis](https://travis-ci.org) build agents).

- [arm64v8/alpine](https://hub.docker.com/r/arm64v8/alpine)
- [qemu-user-static](https://github.com/multiarch/qemu-user-static/releases)
- [anacpe9/docker-arm64v8-alpine-qemu](https://github.com/anacpe9/docker-arm64v8-alpine-qemu)
  - [anacha/arm64v8-alpine-qemu](https://hub.docker.com/r/anacha/arm64v8-alpine-qemu)

## Usage

Before building images from this image or running containers from those on `x86`
architecture execute the following command:

`docker run --rm --privileged multiarch/qemu-user-static:register --reset`

As described in its [GitHub project](https://github.com/multiarch/qemu-user-static)
this will register the *static QEMU binary* that exists in this base image
for all supported processors.

## Layers and Dependencies graph

```text
+-- arm64v8/alpine:3.9
    |
    +-- qemu-aarch64-static:4.0.0
        |
        ` golang:1.12.5
```

| base-3 image  | base-2 image              | base-1 image       |
| ------------- | ------------------------- | ------------------ |
| golang:1.12.5 | qemu-aarch64-static:4.0.0 | arm64v8/alpine:3.9 |
