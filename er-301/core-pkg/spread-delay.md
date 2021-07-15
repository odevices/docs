---
layout: unit
title: Spread Delay
parent: Core Package
grand_parent: ER-301
---

{% include gallery.html
count=2
file1="delay.png"
caption1="mono version"
file2="spread-delay.png"
caption2="stereo version"
%}

## Overview
This unit can only be loaded into stereo chains. It is essentially the same as the [Delay](delay) unit except that it replaces the two independent delay times (left and right delay) with a single shared delay time and a spread value.

{% include pitfall.html
content="This unit will (silently) transform into a regular Delay Unit when loaded into a mono chain."
%}

## Parameters

See the [Delay Unit](delay#parameters) for the other parameters.

### spread
{% include gainbias-control.html %}
This parameter only appears in stereo chains.  The left and right delay times are affected by the spread value in the following manner:

$$
\begin{array}{lcl}
\text{left delay} & = &(1-\text{spread})*\text{delay} \\
\text{right delay} & = & (1+\text{spread})*\text{delay}
\end{array}
$$

For example, if the spread is 0.1, then the Left Delay is shrunk by 10% and the Right Delay is expanded by 10%.  A spread of -0.1 would have the opposite effect. Subtle amounts will "spread" the repeats across the stereo field while more substantial amounts of spread will result in a kind of ping-pong effect.