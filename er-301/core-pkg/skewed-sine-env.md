---
layout: draft-unit
title: Skewed Sine Env
subtitle: A knoll-shaped envelope with apex modulation.
parent: Core Package
grand_parent: ER-301
---

{% include unit-diagram.html 
title="Skewed Sine Env"
pcount = 4
pname1 = "input"
ptype1 = "comparator"
pname2 = "dur"
ptype2 = "gainbias"
pname3 = "skew"
ptype3 = "gainbias"
pname4 = "level"
ptype4 = "gainbias"
%}

## Overview

This AR-type envelope is generated from a single lobe of the sine wave.  Instead of separate controls for attack and release which would complicate setting the duration, there is a skew parameter to lean the envelope left or right, and a parameter to set the total envelope duration.

{% include figure.html
file="skewed-sine-env.png"
%}

## Parameters

### input
{% include comparator-control.html summary="Watches the input for a trigger." %}

This parameter gives you access to the threshold level of the input comparator used to detect the rising edge of the incoming trigger signal.  There is also a button for manually firing triggers.

### dur
{% include gainbias-control.html summary="Envelope duration." %}

This parameter determines the duration of the envelope from start to finish.

### skew
{% include gainbias-control.html summary="Shifts the envelope's apex forward or backward in time." %}

Pulls the apex of the envelope forward (positive skew) or backwards (negative skew).  A good value for a punchy attack with pleasant amount of release is -0.5.

### level
{% include gainbias-control.html summary="Sets envelope amplitude." %}

Sets the height of the envelope's apex.

## See also

* [ADSR](adsr)
* [Envelope Follower](envelope-follower)