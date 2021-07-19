---
layout: draft
title: How to use
parent: Teletype Package
grand_parent: ER-301
nav_order: 1
---

<details open markdown="block">
  <summary>
    Table of contents
  </summary>
  {: .text-delta }
1. TOC
{:toc}
</details>

# Required Hardware Connections 

* First determine your [board revision](/er-301/behind-panel/revisions).
* If you have an ER-301 with board revision 7 (i.e. ER-301 manufactured before June 2018), then please go [here](/er-301/behind-panel/rev7/i2c).
* Otherwise go [here](/er-301/behind-panel/i2c).

# Current Status 
As of v0.3.06 of the ER-301 firmware, there is support for teletype to control the ER-301 over the i2c bus.  There is a discussion thread over on the forum dedicated to this topic:

[Forum thread on teletype integration](https://forum.orthogonaldevices.com/t/i2c-communication-with-monome-teletype/743)

# Available Units and Commands 

{% include pitfall.html
content="ER-301/teletype integration requires ER-301 firmware v0.3.06 or later, and teletype firmware v2.3 or later (discussion and github branch linked [here](https://llllllll.co/t/teletype-2-3-release-beta-1/11232))."
%}

The following commands are available on the teletype for control of the ER-301.  In all cases, the first parameter is the port number which can take any value from 1 to 100. 

|Command|Description|
|---|---|
|SC.TR port α|Set TR value to α (0/1)|
|SC.TR.TOG port|Toggle TR|
|SC.TR.PULSE port|Pulse TR using TO.TR.TIME/S/M as an interval|
|SC.TR.TIME port α|time for TR.PULSE; α in milliseconds|
|SC.TR.POL port α|polarity for TO.TR.PULSE set to α (0-1)|
|SC.CV port α|CV target α (bipolar)|
|SC.CV.SLEW port α|CV slew time; α in milliseconds|
|SC.CV.SET port α|set CV to α (bipolar); ignoring SLEW|
|SC.CV.OFF port α|CV offset; α added at final stage|

(Adapted from: [TELEX Command Reference by bpcmusic](https://github.com/bpcmusic/telex/blob/b0a876b0f63dc125395d47244a72916a25c4a087/commands.md))

The above SC.TR and SC.CV teletype commands are paired with two corresponding units on the ER-301 of the same name:

## SC.TR Unit 
<img src="https://forum.orthogonaldevices.com/uploads/default/original/2X/d/d87c687386295802a462c59e3469ffbbb140e837.png">

The SC.TR unit has a single parameter called 'port' which is also modulate-able.  This port parameter matches the first argument of all of the SC.TR commands on the teletype side.  If desired, you can have multiple units set to the same port.

For example, the following teletype command:

```
SC.TR.PULSE 42
```

will cause **all** instances of SC.TR units with port equal to 42 to output a pulse.  Bang!

## SC.CV Unit 
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

### Value conversions
The teletype maps the integers -16384 to 16384 (*) to the output voltages -10V to 10V.  Since the ER-301, maps the voltages -10V to 10V to the internal values of -1 to 1, ER-301 values are calculated from teletype raw values like this:

$$\mbox{Value in ER-301} = \frac{\mbox{Value in teletype}}{16384}$$

(*) $$16384 = 2^{14}$$

## Selecting Slices 
Two points to consider when using SC.CV and SC.TR commands to select and trigger slices on the ER-301 (or any device that uses a CV/gate selection mechanism).

### Slew
Make sure the CV slew is set to zero (SC.CV.SLEW port 0), or, use the SC.CV.SET command instead of the SC.CV command.  The SC.CV.SET command ignores the slew setting.

### Ordering
Place your SC.TR commands after the SC.CV/SC.CV.SET commands in your teletype script.  At the moment, teletype I2C messages are sent one-by-one and there is no grouping functionality (i.e. here is a bunch of messages to treat as simultaneous).  So the order in which your teletype program generates the messages is the order in which the ER-301 will receive them along with a non-deterministic time interval between the messages (especially if there are a number of devices sharing the i2c bus).

# Configuring the ER-301 
You can enable teletype i2c communication by navigating to Admin > Package Manager, highlight the teletype package and then press 'config' (M6) to enter the teletype configuration screen.

{% include gallery.html
count=2
file1="package-manager.png"
file2="config.png"
%}

Here you can set the ER-301 i2c address.  If you have one ER-301, then use 0x31.  Use 0x32 for your second ER-301 and use 0x33 for your third (!) ER-301.  This way the teletype will automatically route your commands in the following manner: 

|Teletype Port|ER-301 Port|ER-301 Address|
|---|---|---|
|1-100|1-100|0x31|
|101-200|1-100|0x32|
|201-300|1-100|0x33|
