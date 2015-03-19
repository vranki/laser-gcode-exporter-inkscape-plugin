About This Project
------------------

Modified to output gcode that is compatible with K40 style laser cutter
running Marlin (https://github.com/lansing-makers-network/buildlog-lasercutter-marlin).

26-Feb-2015 - 2 hours : Forked from user ajfoul to extend functionality of smoothie  
laser power levels 0.0 to 1.0, generic Marlin power levels being 0 to 100.

07-March-2015 - 10 hours : Cleaned up the exporters code a lot. Added ppm and feedrate detection from the layer name. Updated the gcode that is exported to be neater and work better with pulsed mode using G01, G02 and G03 commands.

07-March-2015 - Fixed the G28 command at the end of the job. Added defaults for laser power, feedrates and ppm if defined. If ppm isn't defined in the layer options it will operate as continuous wave mode. See the help in the extension dialog for how to use.

07-March-2015 - Marlin codebase mod : You need to patch the Marlin codebase to turn on the laser before moving for G02 and G03 commands. This plugin assumes this has been done. More details to come in the future. Copy the code from the G01 above in marlin_main.cpp

19-March-2015 - After optimising the image to gcode 'code' I'm now working on
integrating that into the python script run directly from Inkscape. Hiccups
though as Inkscape for Windows ships with a shitty version of Python that is
missing imaging libraries. Must install Python 2.7 and PIL for image reading.
Have a proof of concept running

20-March-2015 - Added raster support for jpeg and png images. Currently they
export at Inkscape's default DPI of 90, I'll have to upscale them to around
300 next. Go burn some cool shit!

Turnkey Laser Inkscape Gcode Export Plugin
------------------------------------------

This program is an Inkscape extension for exporting a set of paths as 
gcode script. 

This script is a fork of Gcodetools v1.2 written by Nick Drobchenko and
is released under the same license (GPL v2).

Installation
------------

Copy the files turnkeylaser.py and turnkeylaser.inx into your Inkscape extensions
folder. Fire up inkscape and you will find the plugin under Extensions ->
Export -> THLaser GCode Export.

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
