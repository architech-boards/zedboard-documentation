Meta Layer
==========

A Yocto/OpenEmbedded meta-layer is a directory that contains recipes, configuration files, patches, etc., all needed by
*Bitbake* to properly "see" and build a BSP, a distrubution, a (set of) package(s), whatever.
**meta-xilinx** is a meta-layer which defines the BSP for Xilinx devices, ZedBoard included. 
You can get it with *git*:

.. raw:: html

 <div>
 <div><b class="admonition-host">&nbsp;&nbsp;Host&nbsp;&nbsp;</b>&nbsp;&nbsp;<a style="float: right;" href="javascript:select_text( 'meta_layer_rst-host-71' );">select</a></div>
 <pre class="line-numbers pre-replacer" data-start="1"><code id="meta_layer_rst-host-71" class="language-markup">git clone git://git.yoctoproject.org/meta-xilinx.git
 cd meta-xilinx/
 git checkout cb7329a596a5ab2d1392c1962f9975eeef8e4576</code></pre>
 <script src="_static/prism.js"></script>
 <script src="_static/select_text.js"></script>
 </div>

Please, refer to the *README* file contained inside the meta-layer directory.

The machine name corresponding to ZedBoard is **zedboard-zynq7**.