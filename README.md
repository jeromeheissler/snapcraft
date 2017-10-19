# Multiarch Docker image for building Ubuntu snaps.

Based on `multiarch/ubuntu-core` on [Docker Hub](https://hub.docker.com/r/multiarch/ubuntu-core/) and https://github.com/chihchun/snapcraft-docker.

All images are rebuild each week to have packages list updated.

Supported architectures

* amd64 [![Build Status](https://travis-ci.org/jeromeheissler/snapcraft.svg?branch=amd64-xenial)](https://travis-ci.org/jeromeheissler/snapcraft)
* i386 (amd64 architecture) [![Build Status](https://travis-ci.org/jeromeheissler/snapcraft.svg?branch=i386-xenial)](https://travis-ci.org/jeromeheissler/snapcraft)
* armhf (native and amd64 architecture) [![Build Status](https://travis-ci.org/jeromeheissler/snapcraft.svg?branch=armhf-xenial)](https://travis-ci.org/jeromeheissler/snapcraft)
* arm64 (native and amd64 architecture) [![Build Status](https://travis-ci.org/jeromeheissler/snapcraft.svg?branch=arm64-xenial)](https://travis-ci.org/jeromeheissler/snapcraft)

## Usage

Once you need to configure binfmt-support on your Docker host.
This works locally or remotely (i.e using boot2docker or swarm).

```console
# configure binfmt-support on the Docker host (works locally or remotely, i.e: using boot2docker)
$ docker run --rm --privileged multiarch/qemu-user-static:register --reset
```

Then you can run an `armhf` image from your `x86_64` Docker host.

```console
$ docker run -it --rm jeromeheissler/snapcraft:armhf-xenial
```

Or an `x86_64` image from your `x86_64` Docker host, directly, without qemu emulation.

```console
$ docker run -it --rm jeromeheissler/snapcraft:amd64-xenial
```

It also works for `arm64`

```console
$ docker run -it --rm jeromeheissler/snapcraft:arm64-xenial
```
