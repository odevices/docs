---
layout: draft-unit
title: Slew Limiter
subtitle: Limits the rate at which a signal can change.
parent: Core Package
grand_parent: ER-301
---

{% include unit-diagram.html 
title="Slew Limiter"
pcount = 2
pname1 = "time"
ptype1 = "gainbias"
pname2 = "mode"
ptype2 = "option"
%}

## Overview
The purpose of this unit is to limit how fast a signal can change.  However, this unit operates in a very different fashion from the typical (linear) low-pass filter.  The slew limiter tries to track the incoming signal but never changing more than a given rate.  This maximum rate-of-change is determined by the Slew Limiter's time parameter (see below).

Some applications are:
* Pitch glide (fixed rate portamento)
* Rate control
* Turn gates into ramps.

Keep in mind that sometimes what you are really looking for is an [Envelope Follower](envelope-follower).  So please check that out too.

## Parameters

### time
{% include gainbias-control.html summary="Time required to ramp up or down by 1." %}

This time value is use to determine how long it takes for the output value to change by 1 (i.e. full-scale starting at zero).  So if the time value were set to 100ms, and a 0-to-1 step signal were fed to the input of this unit, then output would be a ramp that reaches 1 exactly 100ms after the input signal reached 1.

{% include figure.html
file="slewing-a-step.png"
%}

### mode
{% include option-control.html summary="Apply rate limiting to up, down, or all changes." %}

* **up**: Only apply rate limiting to increases.
* **both**: Apply rate limiting to all changes.
* **down**: Only apply rate limiting to decreases.

## See also

* [Envelope Follower](envelope-follower)