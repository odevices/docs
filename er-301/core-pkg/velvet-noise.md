---
layout: draft-unit
title: Velvet Noise
subtitle: Random (+/-) trigger generator with rate control.
parent: Core Package
grand_parent: ER-301
---

{% include unit-diagram.html
title="Velvet Noise"
pcount=1
pname1="rate"
ptype1="gainbias"
%}

## Overview

Velvet noise is a random train of positive and negative pulses that are each only one sample in length.  Digitally speaking, it is a random sequence of the following three values: -1, 0, and 1.  The rate (and hence the density) of the velvet noise can be controlled by changing the probability that a zero value will be generated.

I first encountered velvet noise when studying reverbation algorithms such as [these](https://www.google.com/search?q=velvet+noise+reverb).

Some applications are:
* Generating random triggers at a target rate.
* A smoother (as in butter) sounding alternative to white noise.
* Popcorn simulator.
* Jazz drum solo generator when used to trigger a drum voice.

## Parameters

### rate
{% include gainbias-control.html %}

The rate parameter controls how often (on average) this unit outputs a trigger.  Each trigger has a 50/50 chance to be positive or negative.  For example, setting the rate to 1Hz means that this unit will a trigger on average once a second.

## See also
* [Pink Noise](pink-noise)
* [White Noise](white-noise)