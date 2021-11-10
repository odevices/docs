---
layout: draft-unit
title: Variable Speed Player
subtitle: Sample player for variable-rate and sliced playback.
parent: Core Package
grand_parent: ER-301
---

## Overview
This unit combines a monophonic resampling play head with a (in-memory) sample buffer.  The main feature of this unit is that the speed of the play head can be sample-accurately modulated up to audio rates.  However, regardless of the values of the speed and V/oct parameters, the unit clamps the final speed to be within the range -64x to 64x (i.e. 6 octaves).

[Slice playback](/er-301/samples/slice-playback) is also included for further control over what parts of the sample buffer are played.

## Parameters

### V/oct
{% include pitch-control.html %}
This parameter is used to transpose the pitch of the sample up or down (in cents) according to an incoming modulation value (typically one of the calibrated inputs from the ABCD matrix).  Its effect *multiplies* the speed parameter like this:  

$$\text{s} = \text{s0} * 2 ^{\frac{x}{1200}}$$

where 

* $$x$$ is the value of this control (in cents)
* $$s0$$ is base speed as set via the speed control
* $$s$$ is the playback speed

For example, if the speed parameter is equal to 0.5x and this V/oct parameter is set to 2400¢, then the resulting sample playback will be 2x (i.e. 2400¢ = 2 octaves which is 4x and the base speed was 0.5x for a total of 2x).  The V/oct parameter is identical in operation to the pitch (or exponential FM) parameter on a VCO.

### speed
{% include gainbias-control.html %}
This parameter controls the base speed of sample playback.  It is called the base speed because the final playback speed will be affected by the V/oct parameter described above. It is similar to the linear FM control on a VCO.  If the V/oct parameter is zero then the sample playback speed is exactly equal to the value of this parameter.  See the V/oct parameter for a complete description of the calculation of sample playback speed.

### gate
{% include comparator-control.html %}
A rising edge on this parameter will cause the play head to reset to either the beginning of the sample or the beginning of the currently selected slice.  The exact meaning of the phrase "beginning of the currently selected slice" depends on the direction of the play head as well as the Slice Polarity setting. Playback continues normally afterwards.

If the Play Duration setting is "loop on gate high" then as long as this parameter receives a high value, the player will loop (i.e. sustain).

If the Play Count setting is "repeat" then a trigger on this parameter can be used to sync the loop to an external event.

### slice
{% include gainbias-control.html %}
This parameter selects a slice.  The next incoming edge received at the [gate](#gate) parameter will activate this slice.  The mapping of parameter value to the actual slice depends on the [Address Mode](#address-mode) setting.

{% include pitfall.html
content="It is often the case that the external signal used to select the slice is delayed with respect to the trigger that is activating the slice.  This will cause inconsistent slice activation (see [this](/er-301/articles/selection-via-cv-gate) for a detailed explanation).  The solution is to insert a small (~2ms) delay in the sub-chain feeding the trigger parameter so that the trigger arrives after the slice selection signal settles.  You can use a [Micro Delay](micro-delay) unit for this purpose."
%}

### shift
{% include gainbias-control.html %}
As stated before, triggering this unit will cause the play head to reset back to the beginning of the sample or to the active slice.  However, if the shift parameter is non-zero then the reset position of the play head will be shifted by a time interval equal to the shift parameter's value.  

For example, if the shift parameter is 1.2s then a trigger will cause the play head to reset to 1.2s into the sample buffer, or in the case of a sliced sample, 1.2s after the active slice.

{% include tip.html 
content="Combine modulation of this parameter with rapid triggering (>10Hz) to simulate modulation of play head position (as opposed to modulation of speed)."
%}

### fade
{% include fader-control.html %}
The output might jump discontinuously when the play head loops at the beginning (ending) of the sample, or, when a trigger resets the play head position.  When this happens, a fade is used smooth over the discontinuity in the output thus suppressing pops.  This parameter sets the length of the fade used.

{% include pitfall.html
content="If you are using a single cycle wave sample to recreate a wavetable oscillator then it is recommended that you set this parameter to zero.  An even better option is to use the [Single Cycle](single-cycle) unit."
%}
