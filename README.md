# odroidn2-android

Basic starting point for upgrading android platforms based on odroidn21.

## Toolchain

For Linux kernel and U-boot, you must install specific toolchains. Android will use its prebuilt ARM toolchain.

Extract the toolchains to /opt/toolchains/

### U-boot
- [Download #1] (http://releases.linaro.org/archive/14.09/components/toolchain/binaries/gcc-linaro-aarch64-none-elf-4.9-2014.09_linux.tar.xz)

- [Download #2](http://releases.linaro.org/archive/14.04/components/toolchain/binaries/gcc-linaro-arm-none-eabi-4.8-2014.04_linux.tar.xz)

### Linux kernel
 - [Download](https://releases.linaro.org/components/toolchain/binaries/6.3-2017.05/aarch64-linux-gnu/gcc-linaro-6.3.1-2017.05-x86_64_aarch64-linux-gnu.tar.xz)

And Please set the PATH to use the toolchains. You should set it before building the Android.


    $ export PATH=$PATH:/opt/toolchains/gcc-linaro-aarch64-none-elf-4.9-2014.09_linux/bin
    $ export PATH=$PATH:/opt/toolchains/gcc-linaro-arm-none-eabi-4.8-2014.04_linux/bin
    $ export PATH=$PATH:/opt/toolchains/gcc-linaro-6.3.1-2017.05-x86_64_aarch64-linux-gnu/bin

## Checkout the Sources

This command will initiate to download the Android source tree for ODROID-N2.
The full source includes u-boot, kernel and Android repositories.

    $ mkdir odroid-n2
    $ cd odroid-n2
    $ repo init -u https://github.com/martinhomuth/odroidn2-android
    $ repo sync

## Build

    $ source build/envsetup.sh
    $ lunch odroidn2-eng
    $ make -j<core number> selfinstall

You can omit the `<core number>` to let the build system choose an appropriate value.

