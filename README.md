# GIT superproject for embedded Qt Linux

The official documentation [Building Your Own Embedded Linux Image](https://doc.qt.io/QtForDeviceCreation/qtee-custom-embedded-linux-image.html) describes a setup depending on the Google repo tool. If you prefer to use a GIT superproject and submodules follow the instructions below.

## Contents

- Restrictions
- Setup
- Build
- Installation

## Restrictions

The official setup supports more than 20 different board types. This setup currently supports Raspberry Pi boards only but you can extend it by adding further submodules.

## Setup

After cloning this repository execute the commands below:

```
cd yocto-boot2qt
git submodule update --init
```
## Build

Check the original documentation for required packages.
Assuming your Raspberry is a model 3 execute the following commands:

```
export MACHINE=raspberrypi3
. setup-environment
bitbake b2qt-embedded-qt5-image
```

## Installation

Insert a SD card suitable for your Raspberry Pi model into your build host.
If it gets automatically mounted unmount it.
Assuming your SD card is visible as /dev/mmcblk0 do the following

```
cd tmp/deploy/images/raspberrypi3
sudo dd if=b2qt-embedded-qt5-image-raspberrypi3.rpi-sdimg of=/dev/mmcblk0 status=progress
```

