About This Fork
---------------

10.14.14 by ajf (https://github.com/ajfoul)

Modified to output gcode that is compatible with K40 style laser cutter
running Marlin
(https://github.com/lansing-makers-network/buildlog-lasercutter-marlin).

I couldn't get the original version from LMN repo to work with LMN's Marlin as
it never set the laser intensity on the M3 command.

This works form me, but YMMV. Very limited testing.  Never leave your laser
cutter unattended while it's powered/operating.  Keep a fire extinguisher
close by, wear saftey goggles, and be afraid! 

USE AT YOUR OWN RISK!

10.17.14 - A little more testing reveals that G02 (CW ARC) and G03 (CCW ARC)
moves are problematic.  Not sure if it's the modifications in this fork, the
original THLaser, LMN's Marlin, Inkscape, or some combination that is causing
the issues. 

Basically, you should consider this pre-alpha code.  Examine the exported
Gcode and do test runs on cardboard/paper before trying to cut on valuable
stock.

Also: G28 at the end of the job doesn't seem to be working at the moment, at
least not when running the gcode on my machine.  

10.19.14 - G02 and G03 really screw things up, so I've set the default
min_arc_radius to 500 to force all cut moves to be G01.  That has it's own
issues.  At this point I wouldn't recommend using the Gcode from this for any
real jobs.

26-Feb-2015 - Forked from user ajfoul to extend functionality of smoothie
laser power levels 0.0 to 1.0, generic Marlin power levels being 0 to 100 and to add in
raster image detection and export support.

THLaser Inkscape Plugin
-----------------------

This program is an Inkscape extension for exporting a set of paths as 
gcode script. 

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
