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
