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

    * automake and autoreconf
      Two programs needed to configure the individual build components automatically.

So for example:

    sudo apt-get install libcap-dev texinfo automake autoreconf

Install cloog
Note that this is required to build the toolchains, no exceptions.  DO NOT install the package libcloog-isl-dev
There is newer versions available that I have compiled as prebuilts to be used in /usr/lib/x86_64-linux-gnu
download it as a zip file from here:
https://github.com/SaberMod/prebuilts_cloog_isl/archive/master.zip

cd to where you have the repository downloaded

    cd ~/Downloads
    unzip prebuilts_cloog_isl-master.zip
    sudo cp -R prebuilts_cloog_isl-master/lib/* -f /usr/lib/x86_64-linux-gnu

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
