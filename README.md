# SV05
Release version 1 of my custom build of Marlin 2.1.1 for the stock Sovol SV05.

This is based of the source code for 2.1.1 at https://github.com/MarlinFirmware

If you just want to install my compiled binary, copy the mysv05-custom-marlin-release_v1.bin to an sd card (make sure there are no other bin files on it).  Make sure your SV05 is turned off, insert the sdcard into the SV05, turn on the SV05.  It will take 10 - 20 seconds to update. The screen will be blank and then the marlin info should come up and the rom boot normally.

IT IS VERY IMPORTANT when changing firmware to reset the EEPROM. It should ask this on startup of my new firmware, but if it doesn't go into the menus on the SV05 and reset the EEPROM.

Features and settings of my firmware.

1) 5x5 Bi-linear bed leveling. (I may switch to UBL in a newer version after some testing)
2) After G28, I have it set to always activate bedleveling. This way you don't need to do it in startup g-code.
3) I heat the hotend to 150 and the bed to 60 before doing any home, bedleveling, tramming, etc. So be aware when you do an initial home on power up, it will home x, home y, and then pause until it heats up. I find 150 give me identical results to 200 and prevents filament from oozing out. Be aware when doing Z offset calibration if you have any filement stuck on the nozzle, you need to remove it with tweezers or whatever so you get a good Z offset
4) Bed tramming wizard. 
5) Host action commands are on (no idea why Sovol had this off). This is useful for Octoprint, etc.
6) Cancel Object is activated ( not really needed if you use Octoprint, but allows you to live cancel objects in a multi-object print). This requires slicer setup to use. If you use Octoprint you can add the exclude region plugin to get the same effect and more.
7) I have power fail resume removed from the firmware. If you need this, let me know and I can add it back. 

I recommend doing a PID tune of the bed and hotend, and calibrating your extruder e-steps after installing my firmware. Just to be sure everything is good for your system. 

My typical operation to level printer. 

1) I do the bed tramming wizard first. This will auto home, heat up bed and nozzle as mentioned above. I then use the LCD to go to each of the four corners and let the probe find the Z difference between center home and that corner. I then turn the bed knob for that corner accordingly and remeasure that point. Getting it as close to zero as possible. I do this for all four corners. After one go through of all four corners, I usually exit this menu and go back in. This re-homes and finds the new Z home value (I find the Z home changes if you make any decent amount of changes with the four bed knobs). I then usually repeat it and find that I have to do small tweaks to get all four corners to as close to 0.00 as possible.  Now your bed is trammed.  You can always do this manually the old school way, but I like this method.

2) After doing #1 above I usually re-home the unit, and then do an auto bed level. I let it go through all 25 points. 

3) I then go under configuration menu, advanced, z offset wizard, and I set the offset to get a little tug on a piece of paper. 

4) Then I go to the save settings on the sv05 menu to save everything above.

5) You can always live adjust your z offset if neeeded and save a better value if you find during your print it isn't where you want it to be.

That is basically it. I welcome any feedback or suggestions.  I do plan on looking into UBL leveling and a few other things, but this has got me printing great prints.
