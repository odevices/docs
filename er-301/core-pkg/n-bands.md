---
layout: draft-unit
title: N Bands
subtitle: Separate the input, process each in a chain, and then mix to output.
parent: Core Package
grand_parent: ER-301
---

{% include gallery.html 
count=2
file1="4-bands.png"
caption1="4 mono bands"
file2="2-stereo-bands.png"
caption2="2 stereo bands"
%}

## Overview

This container unit feeds its input to N chains (i.e. bands) in parallel.  The unit's output is the average of all the bands:

$$\text{OUTPUT} = \frac{\text{BAND}_1(INPUT) + ... + \text{BAND}_N(INPUT)}{N}$$


## Parameters

There are no parameters.  Instead there is one control for each band and pressing the Mx button beneath the control will open the corresponding band's chain.
