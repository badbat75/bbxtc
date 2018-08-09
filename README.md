﻿# ct-ng-configs
Installation:
```
wget http://crosstool-ng.org/download/crosstool-ng/crosstool-ng-1.23.0.tar.xz
tar xf crosstool-ng-1.23.0.tar.xz
cd crosstool-ng-1.23.0
./configure --prefix=/opt/crosstool-ng
make -j4
sudo make install
sudo cp ct-ng.comp /etc/bash_completion.d/
cd ..
```
Start building the crosstool:
```
git clone https://github.com/badbat75/ct-ng-configs
cd ct-ng-configs

DEFCONFIG=./rpi.config ct-ng <config_file>
ct-ng menuconfig
ct-ng build
```
Use the crosstool platform:

Edit bootstrap.conf as needed and run:

```
./bootstrap
```

A new shell will be started with the entire environment set.

Use the crosstool to build kernels:
```
make -j2\
  ARCH=arm \
  CROSS_COMPILE=${C_PREFIX} \
  KBUILD_DEFCONFIG=vexpress_defconfig \
  defconfig
make -j2\
  ARCH=arm \
  CROSS_COMPILE=${C_PREFIX} \
  menuconfig
make -j2 -k\
  ARCH=arm \
  CROSS_COMPILE=${C_PREFIX}
```
