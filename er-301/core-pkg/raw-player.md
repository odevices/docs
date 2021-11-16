---
layout: draft-unit
title: Raw Player
subtitle: The lightest sample player.
parent: Core Package
grand_parent: ER-301
---

{% include unit-diagram.html 
title="Raw Player"
pcount = 5
pname1 = "speed"
ptype1 = "gainbias"
pname2 = "gate"
ptype2 = "comparator"
pname3 = "slice"
ptype3 = "gainbias"
pname4 = "shift"
ptype4 = "gainbias"
pname5 = "fade"
ptype5 = "fader"
%}

## Overview
The Raw Player plays samples at the system rate (48kHz or 96kHz) with no resampling or interpolation (i.e. it just plays the raw samples at 48kHz for the 48kHz firmware and at 96kHz for the 96kHz firmware). This means that only samples which are originally encoded at the system rate (48kHz or 96kHz) will play at the correct pitch and speed. The benefit that comes with this limitation is that samples can be played with minimal CPU load. You can of course, use it to play back samples encoded at any rate, they just won't be playing at their original pitch.

This sample player is great for:
* Achieving the maximum sample polyphony possible on the ER-301.
* Playing sound and automation samples that you recorded on the ER-301 which, by design, already have the correct sample rate needed for this unit.

## Parameters

### speed
{% include gainbias-control.html %}

### gate
{% include comparator-control.html %}

### slice
{% include gainbias-control.html %}

### shift
{% include gainbias-control.html %}

### fade
{% include fader-control.html %}