Yocto for Zedboard by hand
==========================

The easiest way to setup and keep all the necessary meta-layers in sync with upstream repositories
is achieved by means of Google's **repo** tool.
The following steps are necessary for a clean installation:

1) Install repo tool, if you already have it go to step 2

2) Open a terminal

3) Change the current directory to the directory where you want all the meta-layers to be downloaded into

4) Download the manifest

::

 repo init -u https://github.com/architech-boards/zedboard-manifest.git -b dora -m manifest.xml

5) Download the repositories

::

 repo sync

By the end of the last step, all the necessary meta-layers should be in place, anyway, you still need to 
edit your **local.conf** and **bblayers.conf** to compile for zedboard-zynq7 machine and using all the downloaded
meta-layers.

When you want your local repositories to be updated, just:

1) Open a terminal

2) Change the current directory to the directory where you ran repo init

3) Sync your repositories with upstream

::

 repo sync

If you really want to download everything by hand, just clone dora branch of meta-xilinx:

::

 git clone -b dora https://github.com/architech-boards/meta-xilinx.git

and have a look at the README file.

To install *Eclipse*, *Qt Creator*, *cross-toolchain*, *NFS*, *TFTP*, etc., read **Yocto**/**OpenEmbedded** documentation, along
with the other tools one.
