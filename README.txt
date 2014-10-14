
About This Fork
---------------

10.14.14 by ajf (https://github.com/ajfoul)

Modifed to output gcode that is compatible with K40 style laser cutter running Marlin (https://github.com/lansing-makers-network/buildlog-lasercutter-marlin).

I couldn't get the original version from LMN repo to work with LMN's Marlin as it never set the laser intensity on the M3 command.

This works form me, but YMMV. Very limited testing.  Never leave your laser cutter unattended while it's powered/operating.  Keep a fire extinguisher close by, wear saftey googles, and be afraid! 

USE AT YOUR OWN RISK!

THLaser Inkscape Plugin
-----------------------

This program is an Inkscape extension for exporting a set of paths as 
gcode script. It is primarily used by members to the think|haus hacker
space (thinkhaus.org) for use with their laser cutter. As such it is
customized to suit our needs and so may not be your best choice if you
are looking for a general purpose Inkscape to gcode script.

This script is a fork of Gcodetools v1.2 written by Nick Drobchenko and
is released under the same license (GPL v2).

Installation
------------

Copy the files thlaser.py and thlaser.inx into your Inkscape extensions
folder. Fire up inkscape and you will find the plugin under Extensions ->
Export -> THLaser GCode Export.

Keyboard Shortcut
-----------------

You may find it handy to assign the extension to a keyboard shortcut. 
Include something like the following line to your inkscape keys 
preferences file (this will bind the plugin to Ctrl+\):

<bind key="backslash" modifiers="Ctrl" action="org.thinkhaus.filter.thlaser" display="true"/>

You can find your keyboard preferences file:

* On Linux: ~/.config/inkscape/keys/default.xml
* Windows:  %UserProfile%\Application Data\Inkscape\keys\default.xml

If that file doesn't exist, create it and include the following:

<?xml version="1.0"?>
<keys name="My Keys">
<bind key="backslash" modifiers="Ctrl" action="org.thinkhaus.filter.thlaser" display="true"/>
</keys>

