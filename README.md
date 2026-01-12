# Crestron-Shelly
The Crestron-Shelly driver is going through a ground up re-write.  The new
driver will still run on both Crestron 3 and 4 series processors.  The new 
driver significantly improves feedback from Shelly devices by leveraging UDP
messages sent by Shelly devices.  However, this limits the driver to only working
with Generation 2+ Shelly devices.  You will need to use the old driver for 
Generation 1 Shelly devices.

Beta 3 of the driver has now been added to this GitHub.  The new version
adds support for Shelly BLU devices including the TRV, BLU H&T, BLU Button,
and BLU Door/Window Sensor.  These BLU devices require the use of a Shelly
Gen 3 gateway.  Instructions for pairing are included in the BLU modules 
help.  There has also been an update to the Comm Manager module and a 
change to the initialization process.  The demo program includes these 
changes.

Beta 2 of the driver has now been added to this GitHub.  The new version
includes significant improvments to the parsing of UDP messages sent by
Shelly Gen 2+ devices.  It also adds support for Shelly Flood Gen 4 and other 
Gen 2+ devices that generate an alarm output.  It also BEGINS to add support
for the Shelly BLU TRV when connected to a Shelly Gen 3 Blutetooth Gateway.
The driver has been tested with a single TRV and I expect the code to support
the TRV will continue to evolve.  Right now the TRV is the only device that
can connect to the Shelly Gen 3 gateway that is supported.

If you want to try using more than one TRV, then the first should be set to Channel
200, the second to Channel 203, and the third to Channel 206.  I'm talking to 
Shelly to better understand the underlying addressing so I can improve this.

____________________________________________________________________________

This is a first Beta release of the new driver and this first release supports
the following Generation 2+ Shelly devices:
Shelly devies that include one, or more relays.  
Shelly devices that include one, or more switch inputs.
Shelly PM devices that monitor power consumed by connected appliances
Shelly EM devices that monitor energy usage
Shelly Cover devices
Shelly Dimmer devices
Shelly RGB devices
Shelly H&T devices

Unlike the original driver, the new driver's modules are designed to be building
blocks.  For example, for a Shelly PRO 2PM you would use two relay modules, two PM
feedback modules, and two switch input modules.  This paradigm allows users to 
support a wider range of Shelly devices and to only include modules that cover the
features they need.  So, if you don't have switches connected to the inputs of a 
PRO 2PM, then you don't need to add the Switch Input modules to your program.  If
you just have one switch connected to the PRO 2PM, then just use one switch input
module.

The driver has been tested with: Shelly Gen 4 Plug, Shelly PRO 2PM, Shelly EM50,
Shelly PRO Dimmer 2PM, Shelly PRO Dual Cover PM, Shelly PRO RGBWW, Shelly H&T Gen 3.

Once I have feedback and addressed any issues with the new driver code I will begin 
adding support for additonal Shelly products.

Thanks

_____________________________________________________________________________________


Original Crestron-Shelly Driver

The modules in the demo program allow a Crestron 3 or 4 Series Processor to
integrate with Shelly 1, Shelly 1PM, and Shelly 2.5 relays as well as the
Shelly EM energy monitor.  

V2 adds support for the new Shelly Motion detector

V3 adds support for the Shelly Uni

V4 adds support for the Shelly i3

V5 fixes and issue with getting power from a Shelly 1PM and adds support for retreiving voltage readings from
each channel of a Shelly EM.  NOTE- THE POWER_METER_TYPE PARAMETER ON THE SHELLY RELAY MODULE HAS CHANGED
READ THE MODULE'S HELP FILE FOR MORE DETAILS

V7 adds full support for the Shelly RGBW2 module.  NOTE - In implementing this I had to make a change to the Shelly
dimmer S+ file.  If you upgrade to v7 you MUST use the dimmer module included in this build.

V8 corrects issues with the RGBW2, dimmer 2, and roller modules.  It also adds support for the Shelly button,
door-window 2, H&T Sensor, Flood Sensor, and Gas Sensor.  

V9 adds support for the Shelly TRV and Shelly i4.  The Shelly i4 implementation is not fully tested because
I ran into a firmware bug that has been reported to Shelly

V10 updated TRV module to support firmware changes made by Shelly

V11 includes bug fix for the RGBW module.  It also adds support for the Shelly Plug and has been tested with a number 
of newer Shelly Plus and Pro relays

V12 A significant change was made here.  After discussions with Shelly I found that in newer Shelly modules the
security behind usernames/passwords in modules has changed significantly.  They have made it much more secure
and this broke username/password support in the Crestron-Shelly modules.  Because I have not had any 
complaints about this being broken I have decided to simply eliminate the support for usernames/passwords
as these modules are designed for local control (processor to Shelly device) in a residential setting.  So,
username/password parameter fields have been eliminated in all v12 modules.

Other changes in V12 are fixes in the dimmer2 module when it is used to control a Shelly Duo bulb.  Finally,
as requested by a user the dimmer2 module now has outputs for button presses on the switch input.

V13 Fixed a minor bug where the on/off feedback outputs of the dimmer module weren't updating correctly

V14 Added support for the newly announced Shelly Plus H&T Sensor

V15 Fixed bug in dimmer module brightness feedback with dimmer 2

V16 Add support for additional webhooks in the Shelly Motion 2

V17 Added some minor bug fixes and user requests.  The biggest addition is a new module for a project
documented in an article I wrote in Residential Tech Today on motorizing a window using a linear 
actuator.  There is a new Window Control Module and a design described in the article using a Shelly
Plus 1 PM and a Shelly Plus 2 PM.  The operation of these Shelly relays is customized using the 
Javascript files I have added to this repository.  

V18 Fixed bug in relay module reported by user gerrybags

V19 Fixed a bug in the Roller Shade module.  There is a new, v2.1, Roller Shade Module that includes
a poll input as the automatic polling I was trying to do was causing an issue.

V20 Added support for the Shelly Plus Wall Dimmer.  Tested with the Shelly Plus i4 and Shelly Pro 3

V21 Fixes an issue with Shelly devices that have an contact closure input. The input wasn't being 
querried at startup for its current state.  This version also adds support for adjusting white balance
on devices connected to the Shelly-Crestron dimmer module that have support for that feature.  Finally,
it adds support for the upcoming Shelly Add-On.

V23 Adds support for the Shelly Plus Smoke detector and adds a position input to the Shelly 2.5 in Roller
mode

V23.1 - Minimizes header size of messages sent to Shelly TRV to minimize chance of having
messages split into multiple packets which will trigger a firmware bug.

V24 - Adds support for new products released by Shelly including PRO 3EM, PRO EM, PRO EM Add-On Switch

V25 - Adds support for the Shelly display.  Fixes signal allignment in the relay madule.  Adds support
for using gen 2 api commands when communicating with plus/pro relays or plus/pro devices that include
relay functionality as I've seen warnings that gen 1 commands will be removed from these devices in the
future.
PRO Dual Roller PM, Support for Plus 2PM in cover mode, support for new Bluetooth Button and Bluetooth
Door/Window Sensor, and possibly one or two others that I don't specifically remember.  
To use the Bluetooth Button and Bluetooth door/window sensor you need to run the
scripts I have supplied on the Shelly device that is acting as a gateway.  These scripts must be 
customized with the IP address of the crestron processor and the port that is specified in the Shelly
comm manager for receiving messages.

V27 - Add support for Shelly 0-10v dimmer

V28 - Fix bug in reading phase C power from PRO 3EM

V29 - Added support for Shelly Pro EM-50

V30 - Fixed Issue with voltage/power reporting of some EM devices 

V32 - Adds support for BLU H&T and BLU 4 button keypad.  Important - Support for these devices
leverages Shelly's BTHOME technology instead of using custom JavaScripting as was previously 
required to integrate Shelly BLU devices with a Crestron system.  BTHOME only runs on a Shelly
GEN 3 device or a Shelly PRO Device.  There is a good video by Shelly that can walk you 
through the process of getting BTHOME working.  You can find that video here:

https://youtu.be/ojDMNUlaZm4?si=dSLy5Il_0RiqQosd

Once the BLU device is liked to a Shelly GEN 3 or Pro device using BTHOME, it is just a matter
of setting up Action URLs to receive updates from the BLU device. 

V33 - Fixed problem with RGBW Plus module and other misc. bug fixes

Adds support for Shelly BluMotion.  In addition, Shelly made a change that broke the
JavaScript code for all their new Bluetooth devices.  So, the Bluetooth Device Scripts V2.zip
file contains scripts that fix this isue.

V36 Adds support for PLUS TRV, PLUS Uni (using the relay module not the old Uni module
which should now only be used for the original uni), and the PRO RGBWW.  The PRO RGBWW
is only supported when configured as a device profile of light or rgbx2light.  Other
device profiles are not supported.  This version also supports multiple outputs of the
PRO DImmer 2PM.  There are other misc. fixes
