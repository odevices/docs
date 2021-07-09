---
layout: default
title: Power
parent: Behind the Panel
grand_parent: ER-301
nav_order: 13
---

{% include pitfall.html
content="If your board is revision 7 then please go [here](power-rev7) for power information"
%}

# Peak Current Consumption 

|Rail|Peak Current|
|---|---|
|+12V|250mA|
|-12V|30mA|
|+5V|0mA|

Peak Power consumption is about 3.5W.

# Protection and Risks 

The +12V and -12V inputs are protected from reverse-voltage and over-voltage.  However...

If you use your ER-301 without screwing it down to the rails and it falls between the rails into your live powered case, you WILL short various sensitive parts of the rear of the ER-301 to the live voltages of you power bus, and very likely destroy your ER-301.  This really goes for any of your modules.  So please screw your modules in before turning on your case.

{% include figure.html
file="er-301/falling-between-the-rails.jpg"
%}

If your case was on, this module is probably dead now, or, it will fail mysteriously within the next 10 or 20 times that you power it on.
