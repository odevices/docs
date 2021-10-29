---
layout: draft
title: Setup
parent: Teletype Package
grand_parent: ER-301
nav_order: 1
---

## Required Hardware Connections 

* First determine your [board revision](/er-301/behind-panel/revisions).
* If you have an ER-301 with board revision 7 (i.e. ER-301 manufactured before June 2018), then please go [here](/er-301/behind-panel/rev7/i2c).
* Otherwise go [here](/er-301/behind-panel/i2c).


## Configuration
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
