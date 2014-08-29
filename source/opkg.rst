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

.. raw:: html

 <div>
 <div><b class="admonition-board">&nbsp;&nbsp;Board&nbsp;&nbsp;</b>&nbsp;&nbsp;<a style="float: right;" href="javascript:select_text( 'opkg_rst-board-221' );">select</a></div>
 <pre class="line-numbers pre-replacer" data-start="1"><code id="opkg_rst-board-221" class="language-markup">opkg update</code></pre>
 <script src="_static/prism.js"></script>
 <script src="_static/select_text.js"></script>
 </div>

- list available packages:

.. raw:: html

 <div>
 <div><b class="admonition-board">&nbsp;&nbsp;Board&nbsp;&nbsp;</b>&nbsp;&nbsp;<a style="float: right;" href="javascript:select_text( 'opkg_rst-board-222' );">select</a></div>
 <pre class="line-numbers pre-replacer" data-start="1"><code id="opkg_rst-board-222" class="language-markup">opkg list</code></pre>
 <script src="_static/prism.js"></script>
 <script src="_static/select_text.js"></script>
 </div>

- list installed packages:

.. raw:: html

 <div>
 <div><b class="admonition-board">&nbsp;&nbsp;Board&nbsp;&nbsp;</b>&nbsp;&nbsp;<a style="float: right;" href="javascript:select_text( 'opkg_rst-board-223' );">select</a></div>
 <pre class="line-numbers pre-replacer" data-start="1"><code id="opkg_rst-board-223" class="language-markup">opkg list-installed</code></pre>
 <script src="_static/prism.js"></script>
 <script src="_static/select_text.js"></script>
 </div>

- install packages:

.. raw:: html

 <div>
 <div><b class="admonition-board">&nbsp;&nbsp;Board&nbsp;&nbsp;</b>&nbsp;&nbsp;<a style="float: right;" href="javascript:select_text( 'opkg_rst-board-224' );">select</a></div>
 <pre class="line-numbers pre-replacer" data-start="1"><code id="opkg_rst-board-224" class="language-markup">opkg install &lt;package 1&gt; &lt;package 2&gt; ... &lt;package n&gt;</code></pre>
 <script src="_static/prism.js"></script>
 <script src="_static/select_text.js"></script>
 </div>

- list package providing <file>

.. raw:: html

 <div>
 <div><b class="admonition-board">&nbsp;&nbsp;Board&nbsp;&nbsp;</b>&nbsp;&nbsp;<a style="float: right;" href="javascript:select_text( 'opkg_rst-board-225' );">select</a></div>
 <pre class="line-numbers pre-replacer" data-start="1"><code id="opkg_rst-board-225" class="language-markup">opkg search &lt;file&gt;</code></pre>
 <script src="_static/prism.js"></script>
 <script src="_static/select_text.js"></script>
 </div>

- Show package information

.. raw:: html

 <div>
 <div><b class="admonition-board">&nbsp;&nbsp;Board&nbsp;&nbsp;</b>&nbsp;&nbsp;<a style="float: right;" href="javascript:select_text( 'opkg_rst-board-226' );">select</a></div>
 <pre class="line-numbers pre-replacer" data-start="1"><code id="opkg_rst-board-226" class="language-markup">opkg info &lt;package&gt;</code></pre>
 <script src="_static/prism.js"></script>
 <script src="_static/select_text.js"></script>
 </div>

- show package dependencies:

.. raw:: html

 <div>
 <div><b class="admonition-board">&nbsp;&nbsp;Board&nbsp;&nbsp;</b>&nbsp;&nbsp;<a style="float: right;" href="javascript:select_text( 'opkg_rst-board-227' );">select</a></div>
 <pre class="line-numbers pre-replacer" data-start="1"><code id="opkg_rst-board-227" class="language-markup">opkg whatdepends &lt;package&gt;</code></pre>
 <script src="_static/prism.js"></script>
 <script src="_static/select_text.js"></script>
 </div>

- remove packages:

.. raw:: html

 <div>
 <div><b class="admonition-board">&nbsp;&nbsp;Board&nbsp;&nbsp;</b>&nbsp;&nbsp;<a style="float: right;" href="javascript:select_text( 'opkg_rst-board-228' );">select</a></div>
 <pre class="line-numbers pre-replacer" data-start="1"><code id="opkg_rst-board-228" class="language-markup">opkg remove &lt;package 1&gt; &lt;package 2&gt; ... &lt;package n&gt;</code></pre>
 <script src="_static/prism.js"></script>
 <script src="_static/select_text.js"></script>
 </div>

Force Bitbake to install Opkg in the final image
------------------------------------------------

With some images, *Bitbake* (e.g. *core-image-minimal*) does not install the package management system in the final target.
To force *Bitbake* to include it in the next build, edit your configuration file

.. raw:: html

 <div>
 <div><b class="admonition-host">&nbsp;&nbsp;Host&nbsp;&nbsp;</b>&nbsp;&nbsp;<a style="float: right;" href="javascript:select_text( 'opkg_rst-host-41' );">select</a></div>
 <pre class="line-numbers pre-replacer" data-start="1"><code id="opkg_rst-host-41" class="language-markup">/home/architech/architech_sdk/architech/zedboard/yocto/build/conf/local.conf</code></pre>
 <script src="_static/prism.js"></script>
 <script src="_static/select_text.js"></script>
 </div>

and add this line to it:

.. raw:: html

 <div>
 <div><b class="admonition-host">&nbsp;&nbsp;Host&nbsp;&nbsp;</b>&nbsp;&nbsp;<a style="float: right;" href="javascript:select_text( 'opkg_rst-host-42' );">select</a></div>
 <pre class="line-numbers pre-replacer" data-start="1"><code id="opkg_rst-host-42" class="language-markup">IMAGE_FEATURES_append = " package-management"</code></pre>
 <script src="_static/prism.js"></script>
 <script src="_static/select_text.js"></script>
 </div>


Create a repository
-------------------

**opkg** reads the list of packages repositories in configuration files located under */etc/opkg/*. 
You can easily setup a new repository for your custom builds:

1) Install a web server on your machine, for example **apache2**:

.. raw:: html

 <div>
 <div><b class="admonition-host">&nbsp;&nbsp;Host&nbsp;&nbsp;</b>&nbsp;&nbsp;<a style="float: right;" href="javascript:select_text( 'opkg_rst-host-43' );">select</a></div>
 <pre class="line-numbers pre-replacer" data-start="1"><code id="opkg_rst-host-43" class="language-markup">sudo apt-get install apache2</code></pre>
 <script src="_static/prism.js"></script>
 <script src="_static/select_text.js"></script>
 </div>

2) Configure apache web server to "see" the packages you built, for example:

.. raw:: html

 <div>
 <div><b class="admonition-host">&nbsp;&nbsp;Host&nbsp;&nbsp;</b>&nbsp;&nbsp;<a style="float: right;" href="javascript:select_text( 'opkg_rst-host-44' );">select</a></div>
 <pre class="line-numbers pre-replacer" data-start="1"><code id="opkg_rst-host-44" class="language-markup">sudo ln -s /home/architech/architech_sdk/architech/zedboard/yocto/build/tmp/deploy/ipk/ /var/www/zedboard-ipk</code></pre>
 <script src="_static/prism.js"></script>
 <script src="_static/select_text.js"></script>
 </div>

3) Create a new configuration file on the target (for example */etc/opkg/my_packages.conf*) containing lines like this one to index the packages related to a particular machine:

.. raw:: html

 <div>
 <div><b class="admonition-board">&nbsp;&nbsp;Board&nbsp;&nbsp;</b>&nbsp;&nbsp;<a style="float: right;" href="javascript:select_text( 'opkg_rst-board-229' );">select</a></div>
 <pre class="line-numbers pre-replacer" data-start="1"><code id="opkg_rst-board-229" class="language-markup">src/gz zedboard-zynq7 http://192.168.0.100:8000/zedboard-ipk/zedboard-zynq7</code></pre>
 <script src="_static/prism.js"></script>
 <script src="_static/select_text.js"></script>
 </div>

To actually reach the virtual machine we set up a port forwarding mechanism in Chapter :ref:`vm_label` so that every time the board communicates with the workstation on port 8000, VirtualBox actually turns the communication directly to the virtual machine operating system on port 80 where it finds *apache* waiting for it.

4) Connect the board and the personal computer you are developing on by means of an ethernet cable

5) Update the list of available packages on the target

.. raw:: html

 <div>
 <div><b class="admonition-board">&nbsp;&nbsp;Board&nbsp;&nbsp;</b>&nbsp;&nbsp;<a style="float: right;" href="javascript:select_text( 'opkg_rst-board-2210' );">select</a></div>
 <pre class="line-numbers pre-replacer" data-start="1"><code id="opkg_rst-board-2210" class="language-markup">opkg update</code></pre>
 <script src="_static/prism.js"></script>
 <script src="_static/select_text.js"></script>
 </div>

Update repository index
-----------------------

Sometimes, you need to force bitbake to rebuild the index of packages by means of:

.. raw:: html

 <div>
 <div><b class="admonition-host">&nbsp;&nbsp;Host&nbsp;&nbsp;</b>&nbsp;&nbsp;<a style="float: right;" href="javascript:select_text( 'opkg_rst-host-45' );">select</a></div>
 <pre class="line-numbers pre-replacer" data-start="1"><code id="opkg_rst-host-45" class="language-markup">bitbake package-index</code></pre>
 <script src="_static/prism.js"></script>
 <script src="_static/select_text.js"></script>
 </div>