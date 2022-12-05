---
layout: page
title: Quick Start
permalink: /quickstart/
nav_order: 2
---
# Prerequisites

## Hardware requirement

To use Sonica for over-the-air communication with NB-IoT devices,
you need an RF front-end connected. Sonica has been tested with the
following hardware:

* USRP B200, B210
* USRP X300, X310

## Getting Sonica

To get the latest release of Sonica, please visit the [download page](http://metro.cs.ucla.edu/codeshare.html).
The [archive repo](https://github.com/sonica-nbiot/sonica) contains a trial version with basic features.

## Installing dependencies

The main dependencies of Sonica include:
* meson (build system)
* cmake
* FFTW
* MbedTLS
* Boost (Program Options module)
* libconfig (C++ API)
* libsctp
* RF libraries (e.g. UHD for USRP, ZeroMQ for simulation testing, etc.)

To install meson, view <https://mesonbuild.com/Getting-meson.html>

To install other main dependencies on ubuntu (RF libraries not included here):

```sh
$ sudo apt-get install build-essential cmake libfftw3-dev \
   libmbedtls-dev libboost-program-options-dev libconfig++-dev \
   libsctp-dev
```

Sonica does not require using certain specific Linux distribution.
It is tested on Ubuntu 20.04 and Arch Linux.

Building
========
To build Sonica, execute the following commands:

```sh
[sonica]$ meson builddir
[sonica]$ cd builddir
[sonica/builddir]$ meson compile
```

The first line runs the meson configuration script and creates the
subdirectory `builddir` for compilation. In most cases, this only need to
be run once. Subsequent rebuilds only needs `meson compile` in `builddir`
since meson can automatically detect the changes in source files or even
build scripts themselves.

The two binary programs are located within 'builddir' directory:
* eNodeB: `sonica_enb/sonica_enb`
* EPC: `third_party/srsepc_ciot/src/srsepc_ciot`

Configuration
=============
Copy all the files in the `example-config` directory to one of the two locations before running:
* /etc/sonica/ (System-wide configuration)
* ~/.config/sonica (User-specific configuration directory)

Running
=======
Before running the eNodeB, plug in the RF device (e.g. USRP).

After that, first launch the EPC (need root privilege):


```sh
[sonica/builddir]$ sudo ./third_party/srsepc_ciot/src/srsepc_ciot
```

For IP forwarding of EPC network, use `third_party/srsepc_ciot/srsepc_if_masq.sh`
to configure. In most cases, it only needs to be executed once per boot.

Finally, launch eNodeB with:

```sh
[sonica/builddir]$ sonica_enb/sonica_enb
```

If successful, EPC and eNodeB should both print information on the connection
and the eNodeB will start its processing.
