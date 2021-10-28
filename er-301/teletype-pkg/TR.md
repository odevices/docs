---
layout: draft-unit
title: SC.TR
subtitle: Renders the teletype's SC.TR command.
parent: Teletype Package
grand_parent: ER-301
---

# Overview
<img src="https://forum.orthogonaldevices.com/uploads/default/original/2X/d/d87c687386295802a462c59e3469ffbbb140e837.png">

The SC.TR unit has a single parameter called 'port' which is also modulate-able.  This port parameter matches the first argument of all of the SC.TR commands on the teletype side.  If desired, you can have multiple units set to the same port.

For example, the following teletype command:

```
SC.TR.PULSE 42
```

will cause **all** instances of SC.TR units with port equal to 42 to output a pulse.  Bang!

## Teletype Commands
The following commands are available on the teletype for control of this unit.  In all cases, the first parameter is the port number which can take any value from 1 to 100. 

|Command|Description|
|---|---|
|SC.TR port α|Set TR value to α (0/1)|
|SC.TR.TOG port|Toggle TR|
|SC.TR.PULSE port|Pulse TR using TO.TR.TIME/S/M as an interval|
|SC.TR.TIME port α|time for TR.PULSE; α in milliseconds|
|SC.TR.POL port α|polarity for TO.TR.PULSE set to α (0-1)|

(Adapted from: [TELEX Command Reference by bpcmusic](https://github.com/bpcmusic/telex/blob/b0a876b0f63dc125395d47244a72916a25c4a087/commands.md))

