# Crestron-Shelly

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
