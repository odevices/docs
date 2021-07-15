---
layout: unit
title: Linear Bipolar VCA
subtitle: Also known as a ring mod.
parent: Core Package
grand_parent: ER-301
---

{% include gallery.html 
count=2
file1="linear-bipolar-vca.png"
caption1="mono version"
file2="linear-bipolar-vca-stereo.png"
caption2="stereo version"
%}

## Overview
This unit is used to modulate the amplitude of one signal with another signal. Simply put, this unit multiplies the two signals together.  This unit's input signal is multiplied by the value of the level parameter.  The stereo version of this unit adds a panning control.

{% include tip.html
content="Multiplying two signals together is also known as ring modulation where the **input** signal is the carrier and the **level** signal is the modulator."
%}

{% include pitfall.html
content="Experiencing VCA bleed? Use the [unipolar VCA](linear-unipolar-vca) instead.  This bipolar VCA lacks the rectification on the modulation signal that is needed to completely close, especially when using (relatively noisy) externally generated signals."
%}

## Controls

### level 
{% include gainbias-control.html %}

The unit's input is multiplied by the value of this control.

### pan
{% include gainbias-control.html stereo_only=true %}

Pans the signal between the left and right channels according to the following (linear) panning law:

{% include figure.html 
file="/er-301/pan-law.png"
%}

Some examples:
* A value of -1 will hard pan to the left.
* A value of +1 will hard pan to the right.
* A value of zero will pan to the center (no attenuation for both channels).