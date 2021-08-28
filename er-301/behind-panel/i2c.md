---
layout: draft
title: I2C
parent: Behind the Panel
grand_parent: ER-301
---

# What is I2C?

I2C is a hardware bus specification that allows 2 or more integrated circuits to communicate over two wires plus ground.  I2C was designed for *closed systems* where the electrical characteristics of all bus connections and participants are known beforehand.  As an end user, this means you should acknowledge that I2C is not a hardened consumer-oriented technology and all use of I2C to connect the ER-301 to other devices is *at your own risk*.  Using I2C exposes sensitive circuitry of the ER-301 to ESD risks so precautions must be taken when designing your I2C-connected system.  It is best to think of it as a form of community-supported factory-enabled hacking.

# Connecting the Teletype to the ER-301 

{% include pitfall.html
content="If your [board revision](revisions) is revision 7 then you will need to follow different instructions which you can find [here](rev7/i2c)."
%}

In a nutshell, i2c requires 2 communication lines (SCL and SDA) plus 1 ground line.  So there are 3 pins on the Teletype that need to be connected with a custom cable to 3 pins on the ER-301.  Along the bottom edge of the ER-301, you will find an I2C header with 3 pins labeled as GND, SCL, and SDA.  Please connect those pins to the same pins on the Teletype as follows:

* Teletype GND to ER-301 GND.
* Teletype SCL to ER-301 SCL.
* Teletype SDA to ER-301 SDA.

Note that the connections are all one-to-one with no crossovers.

{% include figure.html
width="100%"
file="i2c-wiring.jpg"
%}

{% include tip.html
content="Since the ER-301 does not ship with i2c cables, you will need to make your own or acquire them.  Here is some info on how to DIY your own cables: [DIY i2c cables @ LINES forum](https://llllllll.co/t/diy-i2c-cables/12833?u=odevices)"
%}
