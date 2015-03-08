SaberMod Toolchains Manifest
=====================

License
----------------------

By proceeding, you agree to the terms and conditions of the license.

https://github.com/SaberMod/toolchain_manifest/blob/master/LICENSE

Intro and sources
----------------------

Only supported linux is Ubuntu 14.04-14.10 (Trusty-Utopic).  Branches are separated into master and LTS.  Master branch will be for latest supported Ubuntu version as documented here.  LTS will be for long term support Ubuntu which is currently Ubuntu 14.04 Trusty.  LTS branches will also work on all currently supported systems.
Note: arm-eabi toolchains do not need specific versions of GLIBCXX installed.  They can be used on a variety of linux systems.  These toolchains will most likely not work without modifications to the kernels and the android system.  View all the android source modifications at: https://github.com/SaberMod

Current source components are all from SaberMod github with the exception of upstream merges from gnu and the android open source 
project (aosp)

Toolchain source components separated by branch.  See build scripts to see what versions are being used. https://github.com/SaberMod/sabermod-toolchain-build

    * GCC
      https://github.com/SaberMod/GCC_SaberMod

    * binutils
      based on gnu binutils
      https://github.com/SaberMod/binutils-saber

    * gdb
      based on gnu gdb
      https://github.com/SaberMod/gdb-saber

    * stock gnu binutils and gdb (used for some targets)
      https://sourceware.org/git/gitweb.cgi?p=binutils-gdb.git

    * build
      based on aosp build repo
      https://github.com/SaberMod/toolchain_build

    * SaberMod build scripts
      https://github.com/SaberMod/sabermod-toolchain-build

    * Cloog
      based on gnu cloog
      https://github.com/SaberMod/cloog-current


    * ISL
      based on gnu isl
      https://github.com/SaberMod/isl-current

    * OSL
      based on gnu osl
      https://github.com/SaberMod/osl-saber

    * gmp
      based on gnu gmp
      https://github.com/SaberMod/gnu-gmp
    
    * mpc
      based on gnu mpc
      https://github.com/SaberMod/gnu-mpc

    * mpfr
      based on gnu mpfr
      https://github.com/SaberMod/gnu-mpfr

    * prebuilts
      https://github.com/SaberMod/sm-prebuilts

    * sysroot
      https://github.com/SaberMod/toolchain_sysroot

Prebuilt binary toolchains (in case you don't want to compile your own)
----------------------

kernel toolchains:
Compiled with SaberMod gcc: https://github.com/SaberMod/GCC_SaberMod
https://github.com/SaberMod/arm-eabi-4.8
https://github.com/SaberMod/aarch64-linux-android-4.8
https://gitorious.org/sabermod/arm-eabi-4_9
https://gitorious.org/sabermod/aarch64-linux-android-4_9

android system toolchains (ROM):
Compiled with SaberMod gcc: https://github.com/SaberMod/GCC_SaberMod
https://github.com/SaberMod/arm-androideabi-4.8

Compiled with modified AOSP gcc:
https://github.com/SaberMod/aarch64-linux-android-4.9

Prerequisites - One time step
----------------------

Linux x86_64 - This source only has been tested and works on linux 64bit systems.  Tested on Ubuntu 14.04-14.10 (Trusty-Utopic).

You will need some additional packages to use the included toolchain during compilation.  It is a good idea to make sure you have these packages installed.

Tested on Ubuntu the following packages are available:
    * build-essential
      Essential development packages

    * gcc-multilib g++-multilib

    * flex
      http://flex.sourceforge.net/

    * bison
      http://www.gnu.org/software/bison/

    * libncurses5-dev
      http://download.gna.org/pdbv/demo_html/demo_2.0.10/package/libncurses5-dev_5.4-4.html

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

    sudo apt-get install libcap-dev texinfo automake autoconf libgmp-dev libexpat-dev python-dev build-essential gcc-multilib g++-multilib libncurses5-dev flex bison;

Installing cloog - Can be installed again
----------------------

Note that this is required to build the toolchains, NO EXCEPTIONS.  It is also usefull to have these installed for ROM building with SaberMod.  These help a lot for graphite flags, which you should be using (if not no point in using sm).  DO NOT install the package libcloog-isl-dev
There is newer versions available that I have compiled as prebuilts to be used in /usr/lib/x86_64-linux-gnu
download it as a zip file from here:
https://github.com/SaberMod/sm-prebuilts/archive/master.zip

cd to where you have the repository downloaded

    cd ~/Downloads
    unzip sm-prebuilts-master.zip
    sudo cp -R sm-prebuilts-master/cloog/lib/* -f /usr/lib/x86_64-linux-gnu

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

The build scripts are no longer manitained often unless there is build breakage reported.

cd ~/sm-tc/build-scripts

View all available scripts for targets
-----------------------

    ls

To execute a build for a target
-----------------------

bash "insert name of script"

Checking for updates
-----------------------

    cd ~/sm-tc && repo sync;
