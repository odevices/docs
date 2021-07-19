---
layout: draft-unit
title: Delay
subtitle: A delay line with feedback and wet/dry controls. 
parent: Core Package
grand_parent: ER-301
---

{% include gallery.html
count=2
file1="delay.png"
caption1="mono version"
file2="delay-stereo.png"
caption2="stereo version"
%}

## Overview
Clicks and pops during abrupt changes to the delay time are prevented by rapidly cross-fading between two play heads. Since delay time changes are only applied to the play head that you can't hear, there will be no audible discontinuities. This cross-fade occurs at a rate of approximately 40Hz, which means that the effective delay time (i.e. that you can hear) is only updated once every 25ms.

{% include pitfall.html 
content="This delay line is not interpolated, so actual delay times are rounded to the nearest sample."
%}

## Parameters

### delay
{% include gainbias-control.html %}
This parameter dictates the length of the delay line. In other words, how long it takes for a sound to pass from the input to the output of the Delay unit. The maximum value of this parameter (N) is determined by the Maximum Delay Time setting in the unit's menu.

When this unit is placed in a stereo chain, then the delay parameter is split into separate parameters for the left and right channels.  If you prefer one delay parameter for both channels then replace this unit with the [Spread Delay Unit](spread-delay).

### feedback
{% include gainbias-control.html %}
This value determines how much of the audio in the delay line to mix with the delay's input. A value of 0dB means that the old and new are summed together as-is and will eventually cause the contents of the delay line to grow so loud that it will clip when it arrives at the DAC. A value of {\displaystyle -\infty } means that the new material completely replaces the old material in the delay line. Anything less than 0dB will cause the old material to slowly fade away with each (delayed) repeat. The following graph summarizes the number of repeats required to fade to 10% of the original captured amplitude vs the feedback amount:

{% include figure.html 
file="repeats-vs-feedback.png"
%}

### wet
{% include gainbias-control.html %}
This parameter controls the amount of the input signal and of the affected signal which is passed to the output. A value of 1 (i.e. 100% wet) means you will only hear the affected signal. A value of 0 (i.e. 100% dry) means you will only hear the signal received at the unit's input. However, the cross-fade curve is not linear but rather lifted to counteract the tendency for loudness to dip in the center of a linear cross-fade curve. The actual cross-fade curve looks like this:

{% include figure.html 
file="raised-xfade-law.png"
%}