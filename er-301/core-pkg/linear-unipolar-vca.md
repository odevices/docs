---
layout: unit
title: Linear Unipolar VCA
subtitle: You can never have too many.
parent: Core Package
grand_parent: ER-301
---

{% include gallery.html 
count=2
file1="linear-unipolar-vca.png"
caption1="mono version"
file2="linear-unipolar-vca-stereo.png"
caption2="stereo version"
%}

## Overview
This unit is exactly like the [Linear Bipolar VCA](linear-bipolar-vca) except that the modulation signal is first rectified such that negative modulation is clamped at zero.  If you want to turn a signal "on and off" using another envelope-like signal then this is the VCA that you want.  The rectification helps with shutting off the input signal completely.

### VCA Bleed

Conceptually, envelope generators output 0V when closed.  However, outputting exactly 0V is extremely difficult and even a tiny positive offset and/or thermal noise will likely result in audible VCA bleed.  The typical solution is to design the envelope generator such that it outputs a small negative voltage when closed thereby ensuring that any downstream VCAs are completely closed.  

If your envelope generator has not been designed this way then you can still use this unit because of its builtin offset (i.e. bias) parameter.  In this case, you would set this unit's **level** bias to a small negative value (in the case of a positive envelope) or a small positive value (in the case of a negative envelope), just enough to overcome the envelope's voltage offset and completely close the VCA. You will need to configure this VCA to use positive-half rectification for positive envelopes and negative-half rectification for negative envelopes.

## Settings

### Rectify Type

Here you can choose from the 3 available types of rectification: positive-half, negative-half, and full. The default is positive-half.

## Controls

### level 
{% include gainbias-control.html %}

The unit's input is multiplied by the **rectified** value of this control.  The type of rectification applied can be configured.

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