SaberMod Toolchains Manifest
=====================

Prerequisites
----------------------

You should already have a android build environment set up on Linux

You will need some additional libraries to use the included toolchain during compilation.  It is a good idea to make sure you have these packages installed to assist the graphite flags being used at runtime.

Tested on Ubuntu the following packages are available:

    * libcloog-isl-dev
      Is a set of libraries for graphite that are used during run-time.

    * libcap-dev
      Installs a missing header capability.h file.

    * texinfo
      Program needed to create texi files.
      
So for example:

    sudo apt-get install libcloog-isl-dev libcap-dev texinfo

On Ubuntu 14.04+ you have to link a isl library using root:

    sudo ln -s /usr/lib/x86_64-linux-gnu/libisl.so.10.2.2 /usr/lib/x86_64-linux-gnu/libisl.so.13

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

View all available scripts for targets
----------------------

    ls

Checking for updates
----------------------

    cd ~/sm-tc && repo sync;
