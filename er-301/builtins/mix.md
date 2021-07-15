---
layout: unit
title: Mix
subtitle: A single mixer channel.
parent: Builtin Units
grand_parent: ER-301
---

{% include gallery.html
count=3
file1="mix.png"
caption1="mono-to-mono"
file2="mono-mix.png"
caption2="mono-to-stereo"
file3="stereo-mix.png"
caption3="stereo-to-stereo"
%}

## Overview
This unit (and its variants) allows you to mix the output of an additional sub-chain into any chain at any position. The signal arriving from the left of the Mix unit is added to a panned and attenuated (or amplified) version of the output of the sub-chain associated with the [gain](#gain) parameter. The following diagram depicts the signal flow of the Mix unit. 

{% include figure.html 
file="mix-schematic.png"
%}

Notice how the dB meter taps the signal before the mute choke and gain stage. Also, notice how you can chain multiple Mix units to create a standard mix bus.

## Parameters

### gain
{% include fader-control.html %}
Controls the amount of gain (from -60db to +12db) applied to the signal coming up from the sub-chain before summing it with the input signal (coming in from the left).  When this control is selected, the ER-301 sub-display will also show Solo (S2) and Mute (S3) controls.  The solo/mute group is formed from all the Mix units in the *containing* chain.  So if you had 3 Mixer units in a given chain, pressing solo on one of them will mute the other two and so on.

{% include figure.html
file="mix-solo-example.png"
%}

In the above example, Mix #2 has been solo'ed so that the sub-chain signals going into Mix #1 and #3 have been muted.

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