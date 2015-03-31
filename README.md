About This Project
------------------
This project was intended to build and all in one exporting plugin for laser cutters and Inkscape.
The plugin builds gcode that is compatible with a fork of Marlin designed to run on laser cutters found at https://github.com/TurnkeyTyranny/buildlog-lasercutter-marlin .

You can contact me via email at : 394ad2f@gmail.com


Installation
------------

Copy the files turnkeylaser.py and turnkeylaser.inx into your Inkscape extensions folder -> C:\Program Files\Inkscape\share\extensions
Fire up inkscape and you will find the plugin under Extensions -> Export -> Turnkey Laser Exporter.

This script relies on a more advanced version of the PIL library than Inkscape for windows ships with. As such you need to follow these steps for windows installs of Inkscape 0.91 

* visit https://www.python.org/downloads/ and download python 2.7.9 and install it
* In the folder : C:\Program Files\Inkscape you will need to rename the folder "Python" to "Python-old" so it uses the new system install instead.
* Open up the command line by pressing windows key+r and typing in 'cmd' without the quotes then press enter.
* From the command line, run this command : pip install wheel
* From http://www.lfd.uci.edu/~gohlke/pythonlibs/#pil , download "Pillow-2.7.0-cp27-none-win32.whl" and place it in an easy to navigate to folder
* From the command line, navigate to where you placed that file. If for example you placed it in the C drive you would type without the quotes
* "cd c:\"
* "pip install Pillow-2.7.0-cp27-none-win32.whl"
* You also need to install the libxml library, from the command line run this command without the quotes.
* "easy_install lxml"

Linux Installation
------------------
More fleshed out instructions to come at a later date. Essentially just install the PIL library through yum or apt-get and place the 2 script files (.py and .inx) into your extensions directory.

Usage and Setup
---------------
I recommend starting with this cutting surface and doing your designs in it. Its setup to match the size of the K40 Laser cutter bed : https://github.com/TurnkeyTyranny/laser-gcode-exporter-inkscape-plugin/blob/master/designs/cutting_surface.svg


Alternatively if you're setting up your own new inkscape job first press CTRL+Shift+d, choose the tab called 'page' and set your project units in the 'custom size' area to be 'px'. You can set the 'Default Units' option to be mm, inch or px. The 'Default Units' are the ones displayed on your rulers.

Name your layer in Inkscape like: 10 [feed=600,ppm=40]

This will set the power level to 10%, the feedrate to 600mm per minute and will fire at 40 pulse per millimetre in 60us duration pulses. PPM is ignored for rasters.
The ppm option is optional, if you do not specify it then the laser will default to continuous wave mode.
If you do not name your layer in this way then the script will use the default settings specified in the dialog box.


When you're ready to export your objects, images or paths just select the items you would like to be exported by dragging over them or holding shift to select multiple and then run the plugin under under Extensions Menu -> Export -> Turnkey Laser Exporter. 

Keyboard Shortcut
-----------------

You may find it handy to assign the extension to a keyboard shortcut. 
Include something like the following line to your inkscape keys 
preferences file (this will bind the plugin to Ctrl+\):

<bind key="backslash" modifiers="Ctrl" action="org.thinkhaus.filter.thlaser"
display="true"/>

You can find your keyboard preferences file:

* On Linux: ~/.config/inkscape/keys/default.xml
* Windows:  %UserProfile%\Application Data\Inkscape\keys\default.xml

If that file doesn't exist, create it and include the following:

<?xml version="1.0"?>
<keys name="My Keys">
<bind key="backslash" modifiers="Ctrl" action="org.thinkhaus.filter.thlaser"
display="true"/>
</keys>


Attribution
--------------------
The project is built on work by other people, thanks go out to the effort they put in before me.
Thanks to work by https://github.com/ajfoul , Thinkhaus and Lansing Makers Network
This script is released under the license GPL v2.

Change log
--------------------
26-Feb-2015 - 2 hours : Forked from user ajfoul to extend functionality of smoothie laser power levels 0.0 to 1.0, generic Marlin power levels being 0 to 100.

07-March-2015 - 10 hours : Cleaned up the exporters code a lot. Added ppm and feedrate detection from the layer name. Updated the gcode that is exported to be neater and work better with pulsed mode using G01, G02 and G03 commands.

07-March-2015 - Fixed the G28 command at the end of the job. Added defaults for laser power, feedrates and ppm if defined. If ppm isn't defined in the layer options it will operate as continuous wave mode. See the help in the extension dialog for how to use.

07-March-2015 - Marlin codebase mod : You need to patch the Marlin codebase to turn on the laser before moving for G02 and G03 commands. This plugin assumes this has been done. More details to come in the future. Copy the code from the G01 above in marlin_main.cpp - This change has been put into my version of the Marlin Laser firmware found here https://github.com/TurnkeyTyranny/buildlog-lasercutter-marlin

19-March-2015 - After optimising the image to gcode 'code' I'm now working on integrating that into the python script run directly from Inkscape. Hiccups though as Inkscape for Windows ships with a shitty version of Python that is missing imaging libraries. Must install Python 2.7 and PIL for image reading. Have a proof of concept running

20-March-2015 - Added raster support for jpeg and png images. Currently they export at Inkscape's default DPI of 90, I'll have to upscale them to around 300 next. Go burn some cool shit!

27-March-2015 - Objects in inkscape which are not paths are now exported to be rastered. They are exported at 270dpi. Images are now also upscaled or downscaled and exported at 270dpi.

28-March-2015 - Fixed many many bugs with default power levels and other defaults, completed the work on exporting objects and images as rasters. Fixed up as many situations I could find that threw python error messages and replaced them with meaningful notices for the user.

30-March-2015 - Modified the way that X-Y coordinates are determined for a node. This allows objects that are on a layer that has been transposed or transformed or if the objects themselves have to be correctly positioned in the gcode exported data. It's a little bit slower but much more reliable. This change only applies to the export of rasters.
