---
layout: unit
title: Ladder LPF
subtitle: A low-pass filter with resonance.
parent: Core Package
grand_parent: ER-301
---

{% include figure.html 
file="er-301/core/ladder-lpf.png"
%}

## Overview
This is a digital simulation of the Moog ladder filter in a low-pass configuration with 4-poles (24dB/octave) and non-linear saturation in the feedback loop.  

Frequencies above the cutoff are attenuated while leaving the frequencies below the cutoff (mostly) unchanged.  The cutoff frequency is controlled by the combination of f0 and V/oct controls, while the bandwidth is controlled by the Q control.

This filter will resonate at high values of Q.

{% include filter-controls.md %}

## Special Controls

### Q
{% include gainbias-control.html %}

This parameter controls the filter's resonance. Resonance is the result of a soft-limited feedback path. This parameter sets the gain on that feedback. Higher values of Q (i.e. more feedback) yield a steeper roll-off but cause frequencies around the cut-off to be accentuated.  The filter will resonate at Q-values exceeding 0.5 to 0.6.