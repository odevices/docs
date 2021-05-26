---
layout: default
title: Power (rev 7)
parent: ER-301
nav_order: 13
---

{% include pitfall.html
content="This page is for board revision 7 only.  If your board is [10 or later then please go here for power information](power)."
%}

# 5V Source Selection 
{% include figure.html
file="er-301/5V-source-switch.jpg"
caption="This switch selects the source for +5V power."
%}

The ER-301 has a switch on the back that allows you to select the source of the 5V rail.  The switch has 3 positions:

* USB - Derive 5V from the USB connector.
* REG - Derive 5V from the 12V rail via an internal switching regulator. **This is the recommended setting**.
* BUS - Use the 5V rail directly.  Depending on how your 5V rail is generated this option *might* reduce overall (case-wide) power consumption but there are risks.  See warning below.

# Peak Current Consumption 

|Rail|REG|BUS|
|---|---|---|
|+12V|250mA|130mA|
|-12V|30mA|30mA|
|+5V|0mA|320mA|

The peak power consumption is the same for REG and BUS at about 3.5W.

# Protection and Risks 

The +12V and -12V inputs are protected from reverse-voltage and over-voltage, but the +5V input is **only** protected against reverse-voltage.  

**Warning about BUS mode**<br>
If you plug in a module **other than the ER-301** backwards then the +12V, +5V, and ground rails will all be shorted together.  There have been cases where this has damaged the CPU board and the ER-301 will no longer boot.  Fortunately, the fix is quite easy but requires a small purchase: [Replacing the CPU board](maintenance#replacing-the-cpu-board).

Also...

If you use your ER-301 without screwing it down to the rails and it falls between the rails into your live powered case, you WILL short various sensitive parts of the rear of the ER-301 to the live voltages of you power bus, and very likely destroy your ER-301.  This really goes for any of your modules.  So please screw your modules in before turning on your case.

{% include figure.html
file="er-301/falling-between-the-rails.jpg"
%}

If your case was on, this module is probably dead now, or, it will fail mysteriously within the next 10 or 20 times that you power it on.
