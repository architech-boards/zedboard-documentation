Opkg
====

.. image:: _static/opkg.png
   :align: left

| 
| Opkg (Open PacKaGe Management) is a lightweight package management system. It is written in C and resembles apt/dpkg in operation. It is intended for use on embedded Linux devices and is used in this capacity in the OpenEmbedded and OpenWrt projects. 
| 
|

Useful commands:

- update the list of available packages:

::

  opkg update

- list available packages:

::

  opkg list

- list installed packages:

::

  opkg list-installed 

- install packages:

::

  opkg install <package 1> <package 2> ... <package n> 

- list package providing <file>

::

  opkg search <file>

- Show package information

::

  opkg info <package>

- show package dependencies:

::

  opkg whatdepends <package> 

- remove packages:

::

  opkg remove <package 1> <package 2> ... <package n>


Add a repository
----------------

**opkg** reads the list of packages repositories in configuration files located under */etc/opkg/*. 
You can easily setup a new repository for your custom builds:

1) Install a web server on your machine, for example **apache2**:

::

 sudo apt-get install apache2

2) Configure apache web server to "see" the packages you built, for example:

::

 sudo ln -s /home/architech/architech_sdk/architech/zedboard/yocto/build/tmp/deploy/ipk/ zedboard-ipk

3) Create a new configuration file on the target (for example */etc/opkg/my_packages.conf*) containing lines like this one to index the packages related to a particular machine:

::

 src/gz zedboard-zynq7 http://192.168.0.100/zedboard-ipk/zedboard-zynq7

4) Connect the board and the personal computer you are developing on by means of an ethernet cable

5) Update the list of available packages on the target

::

 opkg update 

Update repository index
-----------------------

Sometimes, you need to force bitbake to rebuild the index of packages by means of:

::

 bitbake package-index
