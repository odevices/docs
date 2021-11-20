---
layout: draft-unit
title: ADSR
subtitle: A traditional 4-stage envelope generator.
parent: Core Package
grand_parent: ER-301
---

{% include unit-diagram.html 
title="ADSR"
pcount = 5
pname1 = "input"
ptype1 = "comparator"
pname2 = "A"
ptype2 = "gainbias"
pname3 = "D"
ptype3 = "gainbias"
pname4 = "S"
ptype4 = "gainbias"
pname5 = "R"
ptype5 = "gainbias"
%}

## Overview
A traditional ADSR envelope with modulate-able controls for the 4 stages: attack time, decay time, sustain level and release time.

{% include figure.html
file="adsr-graph.png"
%}

## Parameters

### input
{% include comparator-control.html summary = "Gate input that starts and ends the envelope." %}
This parameter gives you access to the threshold level of the input comparator used to detect the rising and falling edges of your incoming gate signal. There is also a button for manually firing gates.

### A
{% include gainbias-control.html summary = "Attack time." %}
This parameter sets the (maximum) amount of time it takes for the envelope to ramp up to a value of 1 when it receives a gate signal. The attack portion of the envelope is triggered by a rising edge at the unit input.

### D
{% include gainbias-control.html summary = "Decay time." %}
This parameter sets the (maximum) amount of time it takes for the envelope to decay from 1 to the sustain level.

### S
{% include gainbias-control.html summary = "Sustain level." %}
This parameter sets the amplitude of the sustain portion of the envelope. The decay stage ends at this level and the release stage begins at this level.

### R
{% include gainbias-control.html summary = "Release time." %}
This parameter sets the time it takes for the envelope to fall back to zero. The release portion of the envelope is triggered by a falling edge detected at the unit input.

## See also

* [Skewed Sine Env](skewed-sine-env)
* [Envelope Follower](envelope-follower)