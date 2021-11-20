---
layout: draft-unit
title: Dub Looper
subtitle: Looping sample recorder with control of overdub level.
parent: Core Package
grand_parent: ER-301
---

{% include unit-diagram.html 
title="Dub Looper"
pcount = 7
pname1 = "reset"
ptype1 = "comparator"
pname2 = "engage"
ptype2 = "comparator"
pname3 = "punch"
ptype3 = "comparator"
pname4 = "start"
ptype4 = "gainbias"
pname5 = "fdbk"
ptype5 = "gainbias"
pname6 = "wet"
ptype6 = "gainbias"
pname7 = "fade"
ptype7 = "fader"
%}

## Overview

The Dub Looper combines the input audio with the audio in its buffer like this:

$$
\begin{align}
\mbox{NEW} &= (\mbox{dub}) \times \mbox{INPUT} + (1-\mbox{dub}) \times \mbox{OLD} \\
\mbox{OUTPUT} &= \mbox{XFADE}(NEW,INPUT;\mbox{wet})
\end{align}
$$

where,

* INPUT = the unit input
* OUTPUT = the unit output
* OLD = the previous contents of the buffer
* NEW = the new contents of the buffer
* XFADE(x,y; 0% to 100%) = the crossfade of x and y

In contrast to the [Feedback Looper](feedback-looper) (which can have greater than unity gain), the Dub Looper always has unit gain.  Here are some concrete examples,
* 0% dub means that the existing buffer contents are kept untouched.
* 25% dub means that 25% of the input signal is mixed with 75% of the existing buffer contents.
* 100% dub means that the input completely overwrites the old buffer contents.
* 0% wet means that you only hear the input of the looper and none of the buffer contents.
* 100% wet means that you only hear the output of the looper and none of its input signal. 

The crossfade curve (denoted XFADE in the formula above) is ''lifted'' to compensate for the dip in output volume that results when you use a linear crossfade curve.

## Parameters

### reset
{% include comparator-control.html summary = "Move the play/record head to the start position." %}

A rising edge at this parameter will cause the head to reset to the start position as set by the [start](#start) parameter.  Typically, the start parameter will be zero in which case the head will reset to the beginning of the buffer.

### engage
{% include comparator-control.html summary = "The play/record head advances when engaged." %}

The head advances forward when engaged and does not advance when it is not engaged.  This parameter supports both momentary and latching behaviors.  If the Engage Latch setting is 'on' then this setting behaves like a toggle such that a rising edge engages the head and the following rising edge disengages it.  If the Engage Latch setting is 'off' then the head is only engaged while receiving a high value.

### punch
{% include comparator-control.html summary = "Recording when punched in, not recording when punched out." %}

This parameter is used to punch in or out when recording.  It supports both momentary and latching behaviors.  If the Punch Latch setting is 'on' then this setting behaves like a toggle such that a rising edge punches in and the following rising edge punches out.  If the Punch Latch setting is 'off' then the unit is punched in only while this parameter is receiving a high value.

### start
{% include gainbias-control.html summary = "Sets the reset position." %}

This parameter determines where in the loop buffer the head will reset.  The position is proportional to the total buffer length so that 0 means the beginning of the buffer, 1 means the end, 0.5 means the middle, and so on.  Negative values are supported and wrap around to the end of the buffer so that -0.25 is the same as 3/4 of the way into the buffer.

### dub
{% include gainbias-control.html summary = "Amount of overdub." %}

This parameter determines how much of the input signal should be mixed with the existing buffer contents while keeping a total unity gain.  A dub of 1 (or 100%) means that the input signal completely replaces the existing buffer contents while a dub of 0 (or 0%) leaves the existing buffer contents untouched.  A 25% dub will mix 25% of the input signal with 75% of the existing buffer.

{% include looper-wet-parameter.md %}
{% include fade-parameter.md %}
