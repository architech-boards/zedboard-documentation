Installation
============

Architech's Yocto based SDK is built on top of **Ubuntu 12.04 32bit**, hence all the scripts
provided are proven to work on such a system.


If you wish to use another distribution/version you might need to change some script
option and/or modify the scripts yourself, remember that you won't get any support in
doing so.

Install a clone of the virtual machine inside your native machine
-----------------------------------------------------------------

To install the same tools you get inside the virtual machine on your native machine
you need to download and run a system wide installation script:

.. raw:: html

 <div>
 <div><b class="admonition-host">&nbsp;&nbsp;Host&nbsp;&nbsp;</b>&nbsp;&nbsp;<a style="float: right;" href="javascript:select_text( 'install_scripts_rst-host-211' );">select</a></div>
 <pre class="line-numbers pre-replacer" data-start="1"><code id="install_scripts_rst-host-211" class="language-markup">git clone -b dizzy https://github.com/architech-boards/machine_installer.git
 cd machine_installer
 ./machine_install -g -p</code></pre>
 <script src="_static/prism.js"></script>
 <script src="_static/select_text.js"></script>
 </div>

where *-g* option asks the script to install and configure a few graphic customization,
while *-p* option asks the script to install the required packages on the machine.
If you want to install the toolchain on a machine not equal to Ubuntu 12.04 32bit then
you may want to read the script, install the required packages by hand, and run it without
options. You might need to recompile the Qt application used to render the splashscreen.

At the end of the installation process, you will get the same tools installed within 
the virtual machine, that is, all the tools necessary to work with Architech's boards.

Install just one board
----------------------

If you don't want to install the tools for all the boards, you can install just the subset
of tools related to ZedBoard:

1) Install the following packages, it can require for a while:

.. raw:: html

 <div>
 <div><b class="admonition-host">&nbsp;&nbsp;Host&nbsp;&nbsp;</b>&nbsp;&nbsp;<a style="float: right;" href="javascript:select_text( 'install_scripts_rst-host-212' );">select</a></div>
 <pre class="line-numbers pre-replacer" data-start="1"><code id="install_scripts_rst-host-212" class="language-markup">sudo apt-get update
 sudo apt-get --yes --force-yes install gawk wget git-core diffstat unzip texinfo gcc-multilib build-essential chrpath socat libsdl1.2-dev xterm vim curl u-boot-tools libqtwebkit4 qt4-dev-tools texi2html subversion apache2 autoconf vim-common uuid-dev iasl default-jre libncurses5-dev &gt; /dev/null</code></pre>
 <script src="_static/prism.js"></script>
 <script src="_static/select_text.js"></script>
 </div>

2) Install repo tool, if you already have it go to the next step

.. raw:: html

 <div>
 <div><b class="admonition-host">&nbsp;&nbsp;Host&nbsp;&nbsp;</b>&nbsp;&nbsp;<a style="float: right;" href="javascript:select_text( 'install_scripts_rst-host-213' );">select</a></div>
 <pre class="line-numbers pre-replacer" data-start="1"><code id="install_scripts_rst-host-213" class="language-markup">mkdir -p ~/bin
 sudo apt-get install curl
 curl http://commondatastorage.googleapis.com/git-repo-downloads/repo &gt; ~/bin/repo
 chmod a+x ~/bin/repo</code></pre>
 <script src="_static/prism.js"></script>
 <script src="_static/select_text.js"></script>
 </div>

3) Make sure directory *~/bin* is included in your *PATH* variable by printing its content

.. raw:: html

 <div>
 <div><b class="admonition-host">&nbsp;&nbsp;Host&nbsp;&nbsp;</b>&nbsp;&nbsp;<a style="float: right;" href="javascript:select_text( 'install_scripts_rst-host-214' );">select</a></div>
 <pre class="line-numbers pre-replacer" data-start="1"><code id="install_scripts_rst-host-214" class="language-markup">echo $PATH</code></pre>
 <script src="_static/prism.js"></script>
 <script src="_static/select_text.js"></script>
 </div>

4) If *~/bin* directory is not included, add this line to your *~/.bashrc*

.. raw:: html

 <div>
 <div><b class="admonition-host">&nbsp;&nbsp;Host&nbsp;&nbsp;</b>&nbsp;&nbsp;<a style="float: right;" href="javascript:select_text( 'install_scripts_rst-host-215' );">select</a></div>
 <pre class="line-numbers pre-replacer" data-start="1"><code id="install_scripts_rst-host-215" class="language-markup">export PATH="$PATH:${HOME}/bin"</code></pre>
 <script src="_static/prism.js"></script>
 <script src="_static/select_text.js"></script>
 </div>

5) Install and setup git:

.. raw:: html

 <div>
 <div><b class="admonition-host">&nbsp;&nbsp;Host&nbsp;&nbsp;</b>&nbsp;&nbsp;<a style="float: right;" href="javascript:select_text( 'install_scripts_rst-host-216' );">select</a></div>
 <pre class="line-numbers pre-replacer" data-start="1"><code id="install_scripts_rst-host-216" class="language-markup">sudo apt-get install git-core
 git config --global user.name "Architech User"
 git config --global user.email ""
 git config --global color.ui "auto"</code></pre>
 <script src="_static/prism.js"></script>
 <script src="_static/select_text.js"></script>
 </div>

6) Finally install the board sdk:

.. raw:: html

 <div>
 <div><b class="admonition-host">&nbsp;&nbsp;Host&nbsp;&nbsp;</b>&nbsp;&nbsp;<a style="float: right;" href="javascript:select_text( 'install_scripts_rst-host-217' );">select</a></div>
 <pre class="line-numbers pre-replacer" data-start="1"><code id="install_scripts_rst-host-217" class="language-markup">mkdir ZedBoard
 cd ZedBoard
 git clone -b dizzy https://github.com/architech-boards/zedboard-splashscreen.git
 mv zedboard-splashscreen splashscreen
 cd splashscreen
 ./run_install</code></pre>
 <script src="_static/prism.js"></script>
 <script src="_static/select_text.js"></script>
 </div>

before build an image with bitbake open the file */your/path/ZedBoard/yocto/build/conf/local.conf* and edit these variables:

.. raw:: html

 <div>
 <div><b class="admonition-host">&nbsp;&nbsp;Host&nbsp;&nbsp;</b>&nbsp;&nbsp;<a style="float: right;" href="javascript:select_text( 'install_scripts_rst-host-218' );">select</a></div>
 <pre class="line-numbers pre-replacer" data-start="1"><code id="install_scripts_rst-host-218" class="language-markup">DL_DIR = "/home/downloads"
 SSTATE_DIR = "/home/sstate-cache"</code></pre>
 <script src="_static/prism.js"></script>
 <script src="_static/select_text.js"></script>
 </div>

and change them in:

.. raw:: html

 <div>
 <div><b class="admonition-host">&nbsp;&nbsp;Host&nbsp;&nbsp;</b>&nbsp;&nbsp;<a style="float: right;" href="javascript:select_text( 'install_scripts_rst-host-219' );">select</a></div>
 <pre class="line-numbers pre-replacer" data-start="1"><code id="install_scripts_rst-host-219" class="language-markup">DL_DIR ?= "${TOPDIR}/downloads"
 SSTATE_DIR ?= "${TOPDIR}/sstate-cache"</code></pre>
 <script src="_static/prism.js"></script>
 <script src="_static/select_text.js"></script>
 </div>
