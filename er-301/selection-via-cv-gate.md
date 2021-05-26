---
layout: default
title: Selection via CV/Gate
parent: ER-301
nav_order: 5
---

Making a selection via an external CV signal and a gate signal is a common operation.  However, depending on the source of the CV and gate signals, you might have trouble getting reliable results because you have not insured that the gate (or trigger) is arriving chronologically '''after''' the CV signal has finished transitioning to its newest value.  Here is a diagram that depicts the problem and its solution:

{% include figure.html
file="er-301/selection-via-cv-gate.png"
%}

Assuming you cannot fix the timing at the CV/gate source then you will need to make adjustments in your patch on the ER-301.  Basically, you want to make sure you are not triggering while in the transition period. You can assure your trigger is occurring after the transition period by inserting a [uDelay](core-units/udelay.md) unit into the path of the gate (or trigger) and adjusting the delay time to the smallest value necessary for solid slice selection.

The same situation applies to when you are quantizing to a given clock (say via the Quantize to Clock unit). You need to make sure the CV has already updated by the time your quantize clock releases any pending triggers. In this case, the easiest thing might be to put the delay on the quantize clock, or, after the Quantize to Clock unit. Either way should work. Both is not necessary of course.
