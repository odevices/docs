---
layout: draft-unit
title: Tap Tempo
subtitle: Outputs a clock signal at the most recent tapped rate.
parent: Core Package
grand_parent: ER-301
---

{% include unit-diagram.html
title="Tap Tempo"
pcount = 4
pname1 = "tap"
ptype1 = "comparator"
pname2 = "mult"
ptype2 = "gainbias"
pname3 = "div"
ptype3 = "gainbias"
pname4 = "width"
ptype4 = "gainbias"
%}

## Overview
This unit encapsulates a free-running clock where the rate is read from an incoming clock or tapped in tempo.  The resulting rate can be any integer division and multiplication of the incoming clock.  You also have full independent control over the pulse width and phase (i.e. sync).

Some applications are:
* Divide or multiply an existing clock signal.
* Generate a clock by tapping in a tempo.
* Phase-shift (or re-sync) an existing clock.

## Parameters

### tap
{% include comparator-control.html %}
This parameter represents the input comparator used to tap in or set the clock rate.  Here you can manually tap in the desired clock rate, as well as set the trigger threshold for any incoming (clock) signals.

### mult
{% include gainbias-control.html %}
Use this parameter to set the rate multiplier.  In other words, the clock rate observed at the tap input will be multiplied by this amount to generate the rate used to to create the output clock.

### div
{% include gainbias-control.html %}
Use this parameter to set the rate divider.  In other words, the clock rate observed at the tap input will be divided by this amount to generate the rate used to to create the output clock.

### width
{% include gainbias-control.html %}
Use this parameter to set the output pulse width (or [duty cycle](https://en.wikipedia.org/wiki/Duty_cycle).  Values less than 0.5 cause the high portion of the output clock to be shorter than the low portion, while values more than 0.5 would make the high portion longer than the low portion.  A value of 0.5 results in a 50% duty cycle.
