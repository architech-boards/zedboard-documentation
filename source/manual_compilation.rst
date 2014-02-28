Cross compile from command line
===============================

Yocto/OpenEmbedded can be driven to generate the cross-toolchain for your platform.
There are two common ways to get that:

::

    bitbake meta-toolchain

or

::

    bitbake <image recipe name> -c populate_sdk

The first method provides you the toolchain, you need to provide the file system to compile against,
the second method provides both the toolchain and the file system along with -dev and -dbg packages
installed.

Both ways you get an installation script.

The virtual machine has a cross-toolchain installed for each board, each generated with *meta-toolchain*.
To use it just do:

::

    source /home/architech/architech_sdk/architech/zedboard/toolchain/environment

to compile Linux user-space stuff. If you want to compile kernel or bootloader then do:

::

    source /home/architech/architech_sdk/architech/zedboard/toolchain/environment-nofs

and you are ready to go.
