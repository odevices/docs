---
layout: draft-unit
title: Grain Delay
subtitle: A delay line with a granular playhead for separate control of pitch and speed.
parent: Core Package
grand_parent: ER-301
---

{% include unit-diagram.html
title="Grain Delay"
pcount=4
pname1="delay"
ptype1="gainbias"
pname2="V/oct"
ptype2="pitch"
pname3="speed"
ptype3="gainbias"
pname4="wet"
ptype4="gainbias"
%}

## Description
In the Grain Delay unit, the single read head typically used in other delay units is replaced with multiple read heads, each taking turns to synthesize a train of "audio grains".  Each grain plays interpolated samples at the speed set by the the combination of the speed and V/oct parameters, while the grain production always starts at the head of the delay line.  This means that, unlike other delay units, the delay time and play back speed can be altered independently of each other.

## Parameters

### delay
{% include gainbias-control.html %}
This parameter dictates the length of the delay line. In other words, how long it takes for a sound to pass from the input to the output of the Delay unit. The maximum value of this parameter (N) is determined by the Maximum Delay Time setting in the unit's menu.

When this unit is placed in a stereo chain, then the delay parameter is split into separate parameters for the left and right channels.  

### V/oct
{% include pitch-control.html %}
This parameter is used to transpose the pitch of the grains up or down according to an incoming modulation value (typically one of the calibrated inputs from the ABCD matrix).  Its effect ''multiplies'' the speed parameter like this:  

$$ \text{Playback Speed} = (\text{Base Speed}) * 2 ^{\text{V/oct}} $$

For example, if the speed parameter is equal to 0.5x and this V/oct parameter is set to 2400¢, then the resulting grain playback will be 2x (i.e. 2400¢ = 2 octaves which is 4x and the base speed was 0.5x for a total of 2x).  The V/oct parameter is identical to the pitch (or exponential FM) control on a VCO.

### speed
{% include gainbias-control.html %}
The speed parameter controls the base speed of grain playback.  It is called the base speed because the final playback speed will be affected by the V/oct parameter described above. It is similar to the linear FM control on a VCO.  If the V/oct parameter is zero then the grain playback speed is exactly equal to the value of this parameter.  See the V/oct parameter for a complete description of the calculation of sample playback speed.

### wet
{% include gainbias-control.html %}
This parameter controls the amount of the input signal and of the affected signal which is passed to the output. A value of 1 (i.e. 100% wet) means you will only hear the affected signal. A value of 0 (i.e. 100% dry) means you will only hear the signal received at the unit's input. However, the cross-fade curve is not linear but rather lifted to counteract the tendency for loudness to dip in the center of a linear cross-fade curve. The actual cross-fade curve looks like this:

{% include figure.html 
file="raised-xfade-law.png"
%}

## See also

* [Delay](delay)
* [Doppler Delay](doppler-delay)
* [Spread Delay](spread-delay)
* [Clocked Delay](clocked-delay)
* [Micro Delay](micro-delay)
* [Feedback Looper](feedback-looper)