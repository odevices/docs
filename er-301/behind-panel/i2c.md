---
layout: default
title: I2C
parent: Behind the Panel
grand_parent: ER-301
---

# Connecting the Teletype to the ER-301 

{% include pitfall.html
content="If your [board revision](../revisions) is revision 7 then you will need to follow different instructions which you can find [here](connections-rev7)."
%}

**Please note:** The ER-301 does not ship with i2c cables.  Here is some info on how to DIY your own cables: [DIY i2c cables @ LINES forum](https://llllllll.co/t/diy-i2c-cables/12833?u=odevices).

In a nutshell, i2c requires 2 communication lines (SCL and SDA) plus 1 ground line.  So there are 3 pins on the Teletype that need to be connected with a custom cable to 3 pins on the ER-301.  Along the bottom edge of the ER-301, you will find an I2C header with 3 pins labeled as GND, SCL, and SDA.  Please connect those pins to the same pins on the Teletype as follows:

* Teletype GND to ER-301 GND.
* Teletype SCL to ER-301 SCL.
* Teletype SDA to ER-301 SDA.

Note that the connections are all one-to-one with no crossovers.

{% include figure.html
width="100%"
file="er-301/i2c/rev10/wiring.jpg"
%}
