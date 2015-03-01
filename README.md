SaberMod Toolchains Manifest
=====================

Prerequisites - One time step
----------------------

You will need some additional packages to use the included toolchain during compilation.  It is a good idea to make sure you have these packages installed.

Tested on Ubuntu the following packages are available:
    * build-essential
    * libcap-dev
      Installs a missing header capability.h file.
    * texinfo
      Program needed to create texi files.
    * automake and autoconf
      Two programs needed to configure the individual build components automatically.
    * libgmp-dev
      Needed for cloog to compile (graphite flags tools)
    * libexpat-dev
      Needed for gdb compilation when it uses -lexpat (and it does use it).
    * python-dev
      Needed to use --with-python

So for example:

    sudo apt-get install libcap-dev texinfo automake autoconf libgmp-dev libexpat-dev python-dev build-essential;

Installing cloog - Can be installed again
----------------------

Note that this is required to build the toolchains, NO EXCEPTIONS.  It is also usefull to have these installed for ROM building with SaberMod.  These help a lot for graphite flags, which you should be using (if not no point in using sm).  DO NOT install the package libcloog-isl-dev
There is newer versions available that I have compiled as prebuilts to be used in /usr/lib/x86_64-linux-gnu
download it as a zip file from here:
https://github.com/SaberMod/prebuilts_cloog_isl/archive/master.zip

cd to where you have the repository downloaded

    cd ~/Downloads
    unzip prebuilts_cloog_isl-master.zip
    sudo cp -R prebuilts_cloog_isl-master/lib/* -f /usr/lib/x86_64-linux-gnu

To install future updates, repeat this proccess.

Link header files for multilib - One time step
------------------------------

In order to enable mutilib on ubuntu there's some header files that need to be linked from asm-generic.  asm-generic already has all the files needed but gcc wants it in asm.

    sudo ln -s /usr/include/asm-generic /usr/include/asm;

Create the Directories - One time step
----------------------

    mkdir -p ~/sm-tc && cd ~/sm-tc;

Sync the repo
----------------------

    repo init -u https://github.com/SaberMod/toolchain_manifest -b master
    repo sync

Building toolchains
----------------------

Due to recent copyright infringements from various open source projects, configuring and building the toolchains is now a private resource.  Only people that are wanting to contribute to the project will have access to these.  And will be subject to licensing violations if leaked.  Existing building resources will not be in violation.

Checking for updates
-----------------------

    cd ~/sm-tc && repo sync;
