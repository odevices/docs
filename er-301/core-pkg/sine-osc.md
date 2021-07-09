---
layout: unit
title: Sine Osc
parent: Core Package
grand_parent: ER-301
---


{% include gallery.html 
count=2
file1="er-301/core/sine-osc.png"
file2="er-301/core/sine-osc-f0-expanded.png"
%}

This unit is a full-featured sine oscillator with inputs for both exponential and linear frequency moduleation (FM), phase modulation (PM), amplitude modulation (AM) and feedback. The linear FM supports thru-zero operation.

{% include osc-controls.md %}

## Special Controls

### feedback
{% include gainbias-control.html %}

The feedback parameter determines how much of the unit's (pre-level) output should be used to self-modulate the phase offset.  Increasing amounts of feedback causes the sine wave to morph into a saw-like or ramp-like waveform.

{% include figure.html 
  file = "er-301/core/sine-osc/feedback.gif"
%}

For low frequencies (<55Hz) and high feedback amounts (>0.95), the oscillator will turn chaotic briefly as it passes through zero.

{% include figure.html 
  file = "er-301/core/sine-osc/feedback-chaos.png"
%}

## Applications
* Additive synthesis
* Thru-zero FM synthesis
* Phase Modulation synthesis (PM)
* LFO with sync capabilities
* Follow this unit with a limiter to create a square wave.
* [Waveshaper](https://en.wikipedia.org/wiki/Waveshaper)


{% include osc-tips.md %}