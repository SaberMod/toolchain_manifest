SaberMod Toolchains Manifest
=====================

Prerequisites
----------------------

You should already have a android build environment set up on Linux

You will need some additional libraries to use the included toolchain during compilation.  It is a good idea to make sure you have these packages installed to assist the graphite flags being used at runtime.

Tested on Ubuntu the following packages are available:

    * libcap-dev
      Installs a missing header capability.h file.
    * texinfo
      Program needed to create texi files.

So for example:

    sudo apt-get install libcap-dev texinfo

If you are planning on compiling for arm ROM toolchains you'll need some kernel header files linked to /usr/include
Firt find out what your latest kernel version is.

    ls /usr/src

Output should read simular to this

    bbswitch-0.7                     linux-headers-3.16.0-28-generic
    linux-headers-3.16.0-25          linux-headers-3.16.0-29
    linux-headers-3.16.0-25-generic  linux-headers-3.16.0-29-generic
    linux-headers-3.16.0-26
    linux-headers-3.16.0-26-generic
    linux-headers-3.16.0-28

Go ahead and choose generic to link

    sudo ln -s /usr/src/linux-headers-3.16.0-29-generic/include/asm-generic /usr/include/asm

You can update with new kernel updates if it makes you feel fuzzy inside

    sudo rm -rf /usr/include/asm
    sudo ln -s /usr/src/linux-headers-(version name)-generic/include/asm-generic /usr/include/asm

Create the Directories
----------------------

    mkdir -p ~/sm-tc && cd ~/sm-tc;

Sync the repo
----------------------

    repo init -u https://github.com/SaberMod/toolchain_manifest -b master
    repo sync

Building toolchains
----------------------

To build the SaberMod toolchains enter the scripts directory

    cd ~/sm-tc/build-scripts

Build and install latest versions of cloog and isl
----------------------

These are a set of libraries for graphite flag optimizations that are used during run-time.  Ubuntu does not have these which is why they must compile and install.  This requires root access and will prompt you for your admin password when running this script.

    bash cloog_isl-install

View all available scripts for targets
----------------------

    ls

To execute a build for a target
----------------------

    bash "insert name of script"

Checking for updates
----------------------

    cd ~/sm-tc && repo sync;
