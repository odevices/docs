---
layout: draft-unit
title: Fixed HPF
subtitle: Cheap single-pole highpass filter for removing signal bias or DC.
parent: Core Package
grand_parent: ER-301
---

{% include unit-diagram.html 
title="Fixed HPF"
pcount = 1
pname1 = "freq"
ptype1 = "fader"
%}

## Overview

This is a cheap single-pole high-pass filter that is optimized for set-and-forget scenarios.  Typical uses are:

* Removing DC bias (i.e. centering a signal around zero) to prevent pops or maximize head room.
* Also useful for preventing drift in feedback loops.

## Parameters

### freq
{% include fader-control.html %}

This parameter sets the cut-off frequency of the high-pass filter.

