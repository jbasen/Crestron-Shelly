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
