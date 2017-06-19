docker-build-tools
==================
[![Build Status](https://img.shields.io/travis/trinitronx/docker-build-tools.svg)](https://travis-ci.org/trinitronx/docker-build-tools)
[![Docker Pulls](https://img.shields.io/docker/pulls/trinitronx/build-tools.svg)](https://hub.docker.com/r/trinitronx/build-tools)
[![Docker Stars](https://img.shields.io/docker/stars/trinitronx/build-tools.svg)](https://hub.docker.com/r/trinitronx/build-tools)
[![Gittip](http://img.shields.io/gittip/trinitronx.svg)](https://www.gittip.com/trinitronx)

These are basic docker images starting from official OS base images, and installing `build-essential` packages. Intended for use as base images in further `FROM` directives.

Supported platforms:
--------------------

 - ubuntu-1604
 - ubuntu-1404
 - ubuntu-1204
 - centos-7
 - centos-6
 - alpine-3.6

Packages Installed
------------------

 - CentOS: `yum groupinstall -y "Development Tools"; yum install -y libtool autoconf automake wget gettext which`
 - Ubuntu: `apt-get install -y build-essential libtool automake pkg-config git wget gettext-base`
 - Ubuntu 16.04: `apt-get install -y build-essential libtool libtool-bin automake pkg-config git wget gettext-base`
 - Alpine: `apk add ca-certificates wget build-base git bash autoconf automake libtool gettext openrc && update-ca-certificates`

Image Size
==========


 - `trinitronx/build-tools:ubuntu-1604`: [![Image Layers](https://badge.imagelayers.io/trinitronx/build-tools:ubuntu-1604.svg)](https://imagelayers.io/?images=trinitronx/build-tools:ubuntu-1604 'Get your own badge on imagelayers.io')
 - `trinitronx/build-tools:ubuntu-1404`: [![Image Layers](https://badge.imagelayers.io/trinitronx/build-tools:ubuntu-1404.svg)](https://imagelayers.io/?images=trinitronx/build-tools:ubuntu-1404 'Get your own badge on imagelayers.io')
 - `trinitronx/build-tools:ubuntu-1204`: [![Image Layers](https://badge.imagelayers.io/trinitronx/build-tools:ubuntu-1204.svg)](https://imagelayers.io/?images=trinitronx/build-tools:ubuntu-1204 'Get your own badge on imagelayers.io')
 - `trinitronx/build-tools:centos-7`: [![Image Layers](https://badge.imagelayers.io/trinitronx/build-tools:centos-7.svg)](https://imagelayers.io/?images=trinitronx/build-tools:centos-7 'Get your own badge on imagelayers.io')
 - `trinitronx/build-tools:centos-6`: [![Image Layers](https://badge.imagelayers.io/trinitronx/build-tools:centos-6.svg)](https://imagelayers.io/?images=trinitronx/build-tools:centos-6 'Get your own badge on imagelayers.io')
 - `trinitronx/build-tools:alpine-3.6`: [![Image Layers](https://badge.imagelayers.io/trinitronx/build-tools:alpine-3.6.svg)](https://imagelayers.io/?images=trinitronx/build-tools:alpine-3.6 'Get your own badge on imagelayers.io')

Building
========

To build the images locally, checkout [this repo][1] and run:

    make build
    # OR:
    ./bin/docker-build

Testing
=======

[This repo][1] contains basic `bats` tests to check the built images for the binaries installed.

To run the tests:

    make test

License
=======

[GNU GPL v2](http://choosealicense.com/licenses/gpl-2.0/)

See LICENSE.md for full text

Copyright
=========

Copyright James Cuzella 2014-2017 ([@trinitronx][trinitronx-keybase])

[1]: https://github.com/trinitronx/docker-build-tools
[trinitronx-keybase]: https://gist.github.com/trinitronx/aee110cbdf55e67185dc44272784e694
