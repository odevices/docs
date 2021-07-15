---
layout: unit
title: Micro Delay
subtitle: A cheap delay for very small delay times.
parent: Core Package
grand_parent: ER-301
---

{% include figure.html 
file="micro-delay.png"
%}

## Overview
This utility unit is just a very short fixed delay line. Whatever goes in, comes out a short time later (0 to 10ms). It's very light on the CPU and consumes almost no memory.

Some application are:
* Delaying triggers or gates a few milliseconds so that an associated CV signal has time to settle on its target value.  See [Selection via CV/Gate](/er-301/articles/selection-via-cv-gate) for more details.
* Delaying the sync trigger on Looper that is writing to a shared buffer, so that it doesn't clobber a player unit sharing the same buffer and sync signal.
* Useful anywhere a small fixed delay is needed with as small a CPU load and memory footprint as possible.

## Parameters

### delay
{% include fader-control.html %}

This fader sets the delay time.  If you want a modulate-able delay then please use the regular [Delay Unit](delay).