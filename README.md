# Crestron-Shelly
The Crestron-Shelly driver has gone through a ground up re-write.  The new
driver will still runs on both Crestron 3 and 4 series processors.  The new 
driver significantly improves feedback from Shelly devices by leveraging UDP
messages sent by Shelly devices.  However, this limits the driver to only working
with Generation 2+ Shelly devices.  You will need to use the old driver for 
Generation 1 Shelly devices.

v1.1 - Added support for Shelly Presence Sensor Gen 4, Shelly i4/i4 DC Gen 4,
and Shelly Power Strip 4 Gen 4.

v1.01 - Added channel numbers of 100+ to the temperature and humidity sensor
modules to support their use with temperature and humidity add-ons to other
devices.  This is demonstrated with the smart water valve in the demo program.

v1 - Supports the following Shelly devices:

Shelly devices that include one, or more relays

Shelly devices that include one, or more switch inputs

Shelly PM devices that monitor power consumed by connected appliances

Shelly EM devices that monitor energy usage

Shelly Cover devices

Shelly Dimmer devices

Shelly RGB devices

Shelly H&T devices

Shelly Flood Gen 4 and other Gen 2+ devices that generate an alarm output

Shelly Smart Water Valve

Shelly Irrigation Controller

BLU Wall Switch 4

BLU RC Button 4 US ZB

BLU H&T Display ZB

BLU TRV

BLU H&T

BLU Button

BLU Door/Window Sensor

BLU Weather Station

Unlike the original driver, the new driver's modules are designed to be building
blocks.  For example, for a Shelly PRO 2PM you would use two relay modules, two PM
feedback modules, and two switch input modules.  This paradigm allows users to 
support a wider range of Shelly devices and to only include modules that cover the
features they need.  So, if you don't have switches connected to the inputs of a 
PRO 2PM, then you don't need to add the Switch Input modules to your program.  If
you just have one switch connected to the PRO 2PM, then just use one switch input
module.

The driver has been tested with: Shelly Gen 4 Plug, Shelly PRO 2PM, Shelly EM50,
Shelly PRO Dimmer 2PM, Shelly PRO Dual Cover PM, Shelly PRO RGBWW, Shelly H&T Gen 3,
and the above mentioned Shelly devices.

Some behavior issues were found with the Shelly BLU H&T Display ZB and the Shelly
Weather Station.  The Shelly Weather Station doesn't report all measured 
data through the API.  For example, temperature, humidity, and pressure are not
reported through the API while wind speed is.  These have been reported to Shelly.

I have also noticed that the Shelly H&T Gen 3 is very stingy when it comes to sending
data out through the API.  Even at powerup the device doesn't send out a data update.

All BLU modules have been tested by pairing them with the Shelly Gen3 Bluetooth
Gateway.  Pairing Shelly BLU devices through any other Shelly devices has not been
tested.  

It is very important that Shelly BLU devices be paired with the gateway
using the gateway's web page.  If you perform the pairing with the Shelly app 
the pairing will not work properly and you won't be able to gather data from
the Shelly BLU device or control it.  Please carefully read the help by
pressing F1 in SimplWindow when the S+ modules are selected.

The Shelly_UDP S# v1.zip is the full C#/S# source code for this driver. 
Becase the driver will run on both Crestron 3-Series and 4-Series 
processors, you will need VS2008 to compile this code.

With the release of this driver there won't be any futher updates or
bug fixes to the original Shelly driver.  Over time, with the support
of multiple versions of the Shelly API, the driver code has become
very convoluted and changes are extremely difficult.

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
