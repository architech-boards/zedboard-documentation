Yocto based SDK
===============

The SDK provided by *Architech* to support Zedboard is composed by several components, the most important of which are:

* **Yocto**,

* **Eclipse**, and

* **Qt Creator**

Regarding the installation and configuration of these tools, you have many options:

1) get a virtual machine with everything already setup,

2) download a script to setup your Ubuntu machine, or

3) just get the meta-layer and compose your SDK by hand

The method you choose depends on your level of expertise and the results you want to achieve.

If you are new to **Yocto** and/or **Linux**, or simply you don't want to read tons of documentation right now,
we suggest you to download and :ref:`install the virtual machine <vm_label>` because it is the simplest solution
(have a look at :ref:`vm-layout_label`), everything inside the virtual machine has been thought to work out of the
box, plus you will get support.

If performances are your greatest concerns you can install everything on a native machine, how you do it depends on
your level of expertise in Linux/Yocto, the time you have available to make everything work and the level of customization
you want to achieve. If you just care about speed, then :ref:`download a script from the Internet and start to work <install_scripts_label>`.

If you prefer to install Yocto meta-layers by hand, please have a look at this how to on
:ref:`installing Yocto for Zedboard by hand <yocto_by_hand_label>`.
