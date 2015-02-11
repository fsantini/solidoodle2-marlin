#Marlin firmware for Solidoodle 2/3
Previous official Solidoodle firmware was based on early version of Marlin and could not be altered to accomodate a Panelolu LCD screen and encoder without many errors. This version has configuration.h and configuration_adv.h altered to reflect all changes found in official Solidoodle firmware.
Marlin has a GPL license because I believe in open development.
##Step 1

You need to have the Arduino0022 IDE installed. If you have a later version, you'll need to downgrade.
Download from:
-http://arduino.cc/hu/Main/Software

*Arduino0022 is no longer needed.* A preprepared version of Arduino 1.0.5 has been setup by ozadr1an. It features the required changes needed for the Sanguinololu electronics to work with versions of Arduino beyond 0022.
Official Arduino download is available, but you will need to move the files from the Add-ons folder of this repository for the firmware to successfully compile and upload:

-http://arduino.cc/hu/Main/Software

###Preprepared PC version:

-http://www.mediafire.com/download/leatx20mqiicipz/Solidoodle-arduino-1.0.5-windows.zip
-https://docs.google.com/file/d/0B7IeeziM0bp9S3FMQUM2Rk02ajQ

Simply unzip into a folder of your choice.

###Preprepared Mac version:

-http://www.mediafire.com/download/9z357ec4rrwpfu7/Solidoodle-arduino-1.0.5-macosx.zip
-https://docs.google.com/file/d/0B7IeeziM0bp9Yjd4SFZfb0QwZ0U

###PC Users:

(Original version of Arduino022 already setup for this firmware is now available again at: http://www.mediafire.com/?3qy0wjf86a66du8 .)

Simply unzip into a folder of your choice.

Skip to step 4.

##Step 2 (Mac only)

Clone the repository at
-https://github.com/jmgiacalone/sanguino1284p
and copy the included Sanguino directory to the hardware directory of your Arduino install. On Mac OS X, that would be ~/Documents/Arduino/hardware.


##Step 3 (Mac only)

Close the Arduino IDE and then copy the file avrdude.conf from the sanguino1284p clone to your ~/Documents/Arduino/hardware/tools/avr/etc.
Start the Arduino IDE and you should now see 'Sanguino W/ ATmega644P' AND 'Sanguino W/ ATmega1284P' options in the Tools->Board menu.

##Step 4

If you have a Solidoodle 2, then the firmware is already setup for you by default.
If you have a Solidodle 3, simply change line 15 in configuration.h from:
```C
#define SOLIDOODLE_VERSION 2
```
to:
```C
#define SOLIDOODLE_VERSION 3 
```

##Step 5

For the standard Solidoodle 2/3 model with the 644P microcontroller, upload the firmware as is and select the 'Sanguino W/ ATmega644P' option.

##Step 6

If you're adding an SDSL SDCARD reader, or Panelolu LCD display and rotary encoder with SDSL, you will need to select the 'Sanguino W/ ATmega1284P' board. Please purchase a 1284P with a bootloader already in place.

For a Panelolu/SD card reader combo, uncomment line 316 in configuration.h from:
```C
//#define ULTIPANEL  //the ultipanel as on thingiverse
```
to:
```C
#define ULTIPANEL  //the ultipanel as on thingiverse
```
Now compile and upload.

-http://www.soliforum.com/topic/127/panelolu-complete-guide/
-http://www.emakershop.com/browse/listing?l=280
-http://www.emakershop.com/browse/listing?l=307
-http://blog.think3dprint3d.com/2012/06/panelolu-in-depth.html

If you're only adding SDSL, uncomment line 313 in configuration.h from:

```C
//#define SDSUPPORT // Enable SD Card Support in Hardware Console
```
to:
```C
#define SDSUPPORT // Enable SD Card Support in Hardware Console
```

Now compile and upload.

-http://reprap.org/wiki/SDSL
-http://www.emakershop.com/browse/listing?l=182

##Original Marlin Readme:
Copy the Marlin firmware

  * [Configuration & Compilation](/Documentation/Compilation.md)
  * Supported
    * [Features](/Documentation/Features.md)
    * [Hardware](/Documentation/Hardware.md)
    * [GCodes](/Documentation/GCodes.md)
  * Notes
    * [Auto Bed Leveling](/Documentation/BedLeveling.md)
    * [Filament Sensor](/Documentation/FilamentSensor.md)
    * [Ramps Servo Power](/Documentation/RampsServoPower.md)

##### [RepRap.org Wiki Page](http://reprap.org/wiki/Marlin)

## Quick Information

This is a firmware for reprap single-processor electronics setups.
It also works on the Ultimaker PCB. It supports printing from SD card+Folders, and look-ahead trajectory planning.
This firmware is a mashup between [Sprinter](https://github.com/kliment/Sprinter), [grbl](https://github.com/simen/grbl) and many original parts.

## Current Status: Bug Fixing

The Marlin development is currently revived. There's a long list of reported issues and pull requests, which we are working on currently.
We are actively looking for testers. So please try the current development version and report new issues and feedback.

[![Coverity Scan Build Status](https://scan.coverity.com/projects/2224/badge.svg)](https://scan.coverity.com/projects/2224)
[![Travis Build Status](https://travis-ci.org/MarlinFirmware/Marlin.svg)](https://travis-ci.org/MarlinFirmware/Marlin)

What bugs are we working on: [Bug Fixing Round 2](https://github.com/MarlinFirmware/Marlin/milestones/Bug%20Fixing%20Round%202)

## Contact

__IRC:__ #marlin-firmware @freenode ([WebChat Client](https://webchat.freenode.net/?channels=marlin-firmware), [Archive](http://energymonitor-dk.dns4e.net/marlin-firmware-log/))

__Mailing List:__ marlin@lists.0l.de ([Subscribe](http://lists.0l.de/mailman/listinfo/marlin), [Archive](http://lists.0l.de/pipermail/marlin/))

## Credits

The current Marlin dev team consists of:

 - Erik van der Zalm ([@ErikZalm](https://github.com/ErikZalm))
 - [@daid](https://github.com/daid)
 
Sprinters lead developers are Kliment and caru.
Grbls lead developer is Simen Svale Skogsrud.
Sonney Jeon (Chamnit) improved some parts of grbl
A fork by bkubicek for the Ultimaker was merged.

More features have been added by:
  - Lampmaker,
  - Bradley Feldman,
  - and others...

## Licence

Marlin is published unde the [GPL license](/Documentation/COPYING.md) because I believe in open development.
Please do not use this code in products (3D printers, CNC etc) that are closed source or are crippled by a patent.

[![Flattr this git repo](http://api.flattr.com/button/flattr-badge-large.png)](https://flattr.com/submit/auto?user_id=ErikZalm&url=https://github.com/MarlinFirmware/Marlin&title=Marlin&language=&tags=github&category=software)
