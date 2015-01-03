SaberMod Toolchains Manifest
=====================

Prerequisites
----------------------

You should already have a android build environment set up on Linux

You will need some additional libraries to use the included toolchain during compilation.  It is a good idea to make sure you have these packages installed.

Tested on Ubuntu the following packages are available:

    * libcap-dev
      Installs a missing header capability.h file.

    * texinfo
      Program needed to create texi files.
      
So for example:

    sudo apt-get install libcap-dev texinfo

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

To execute a build for a target
----------------------

bash "insert name of script"

Checking for updates
----------------------

    cd ~/sm-tc && repo sync;
