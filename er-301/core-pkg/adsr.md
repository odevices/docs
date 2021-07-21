---
layout: draft-unit
title: ADSR
subtitle: A traditional 4-stage envelope generator.
parent: Core Package
grand_parent: ER-301
---


{% include figure.html 
file="adsr.png"
%}

## Overview
A traditional ADSR envelope with modulate-able controls for the 4 stages: attack time, decay time, sustain level and release time.

{% include figure.html
file="adsr-graph.png"
%}

## Parameters

### input
{% include comparator-control.html %}
This parameter gives you access to the threshold level of the input comparator used to detect the rising and falling edges of your incoming gate signal. There is also a button for manually firing gates.

### attack
{% include gainbias-control.html %}
This parameter sets the (maximum) amount of time it takes for the envelope to ramp up to a value of 1 when it receives a gate signal. The attack portion of the envelope is triggered by a rising edge at the unit input.

### decay
{% include gainbias-control.html %}
This parameter sets the (maximum) amount of time it takes for the envelope to decay from 1 to the sustain level.

### sustain
{% include gainbias-control.html %}
This parameter sets the amplitude of the sustain portion of the envelope. The decay stage ends at this level and the release stage begins at this level.

### release
{% include gainbias-control.html %}
This parameter sets the time it takes for the envelope to fall back to zero. The release portion of the envelope is triggered by a falling edge detected at the unit input.
