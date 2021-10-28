---
layout: draft-unit
title: SC.CV
subtitle: Renders the teletype's SC.CV command.
parent: Teletype Package
grand_parent: ER-301
---

# Overview
<img src="https://forum.orthogonaldevices.com/uploads/default/original/2X/2/25e354d46318c861922bea3eb3d15972ca6f7863.png">

The SC.CV unit has a single parameter called 'port' which is also modulate-able.  This port parameter matches the first argument of all of the SC.CV commands on the teletype side.  If desired, you can have multiple units set to the same port.

For example, **any** of the following teletype commands:

```
SC.CV 42 N 12
SC.CV 42 V 1
SC.CV 42 VV 100
SC.CV 42 1638
```

will cause **all** instances of SC.TR units with port equal to 42 to slew to the value of 0.1 (which corresponds to the external value of 1V).  

## Teletype Commands
The following commands are available on the teletype for control of this unit.  In all cases, the first parameter is the port number which can take any value from 1 to 100. 

|Command|Description|
|---|---|
|SC.CV port α|CV target α (bipolar)|
|SC.CV.SLEW port α|CV slew time; α in milliseconds|
|SC.CV.SET port α|set CV to α (bipolar); ignoring SLEW|
|SC.CV.OFF port α|CV offset; α added at final stage|

(Adapted from: [TELEX Command Reference by bpcmusic](https://github.com/bpcmusic/telex/blob/b0a876b0f63dc125395d47244a72916a25c4a087/commands.md))

## Value conversions
The teletype maps the integers -16384 to 16384 (*) to the output voltages -10V to 10V.  Since the ER-301, maps the voltages -10V to 10V to the internal values of -1 to 1, ER-301 values are calculated from teletype raw values like this:

$$\mbox{Value in ER-301} = \frac{\mbox{Value in teletype}}{16384}$$

(*) $$16384 = 2^{14}$$

## Selecting Slices 
Two points to consider when using SC.CV and SC.TR commands to select and trigger slices on the ER-301 (or any device that uses a CV/gate selection mechanism).

### Slew
Make sure the CV slew is set to zero (SC.CV.SLEW port 0), or, use the SC.CV.SET command instead of the SC.CV command.  The SC.CV.SET command ignores the slew setting.

### Ordering
Place your SC.TR commands after the SC.CV/SC.CV.SET commands in your teletype script.  At the moment, teletype I2C messages are sent one-by-one and there is no grouping functionality (i.e. here is a bunch of messages to treat as simultaneous).  So the order in which your teletype program generates the messages is the order in which the ER-301 will receive them along with a non-deterministic time interval between the messages (especially if there are a number of devices sharing the i2c bus).
