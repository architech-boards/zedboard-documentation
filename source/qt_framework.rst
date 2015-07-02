.. _qt_framework_label:

Qt cross-toolchain
==================

The Qt Framework used by this SDK is composed of libraries for your host machine and your target.
To compile the libraries for *x86* you only need your distribution toolchain, while to compile the
libraries for ZedBoard board you need the proper cross-toolchain (see Chapter :ref:`manual_compilation_label`
for further information on how to get it).

First of all you need to compile the cross-toolchain with Yocto: 

.. raw:: html

 <div>
 <div><b class="admonition-host">&nbsp;&nbsp;Host&nbsp;&nbsp;</b>&nbsp;&nbsp;<a style="float: right;" href="javascript:select_text( 'qt_framework_rst-host-41' );">select</a></div>
 <pre class="line-numbers pre-replacer" data-start="1"><code id="qt_framework_rst-host-41" class="language-markup">bitbake meta-toolchain-qte</code></pre>
 <script src="_static/prism.js"></script>
 <script src="_static/select_text.js"></script>
 </div>

The recipe builds **poky-glibc-i686-meta-toolchain-qte-armv7a-vfp-neon-toolchain-qte-1.7.1.sh** installation script.
You should find the installation script in */home/architech/architech_sdk/architech/zedboard/yocto/build/tmp/deploy/sdk*.
The cross-toolchain allows to compile a Qt embedded 4.8.5 application.

To install the toolchain run the following commands:

.. raw:: html

 <div>
 <div><b class="admonition-host">&nbsp;&nbsp;Host&nbsp;&nbsp;</b>&nbsp;&nbsp;<a style="float: right;" href="javascript:select_text( 'qt_framework_rst-host-42' );">select</a></div>
 <pre class="line-numbers pre-replacer" data-start="1"><code id="qt_framework_rst-host-42" class="language-markup">sudo ./poky-glibc-i686-meta-toolchain-qte-armv7a-vfp-neon-toolchain-qte-1.7.1.sh</code></pre>
 <script src="_static/prism.js"></script>
 <script src="_static/select_text.js"></script>
 </div>

The installation script will ask to select an installation path.

.. raw:: html

 <div>
 <div><b class="admonition-host">&nbsp;&nbsp;Host&nbsp;&nbsp;</b>&nbsp;&nbsp;<a style="float: right;" href="javascript:select_text( 'qt_framework_rst-host-43' );">select</a></div>
 <pre class="line-numbers pre-replacer" data-start="1"><code id="qt_framework_rst-host-43" class="language-markup">sudo chown -R architech:architech ~/path/to/toolchain/installed</code></pre>
 <script src="_static/prism.js"></script>
 <script src="_static/select_text.js"></script>
 </div>

Before to run Qt creator you must set the environment variables:

.. raw:: html

 <div>
 <div><b class="admonition-host">&nbsp;&nbsp;Host&nbsp;&nbsp;</b>&nbsp;&nbsp;<a style="float: right;" href="javascript:select_text( 'qt_framework_rst-host-44' );">select</a></div>
 <pre class="line-numbers pre-replacer" data-start="1"><code id="qt_framework_rst-host-44" class="language-markup">source /opt/poky/1.7.1/environment-setup-armv7a-vfp-neon-poky-linux-gnueabi
 source /opt/poky/1.7.1/sysroots/i686-pokysdk-linux/environment-setup.d/qtopia.sh</code></pre>
 <script src="_static/prism.js"></script>
 <script src="_static/select_text.js"></script>
 </div>

.. note::

 | qtopia.sh is used to allow the compilation for the **qt4e-demo-image**