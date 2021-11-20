---
layout: draft-unit
title: Counter
subtitle: 
parent: Core Package
grand_parent: ER-301
---

{% include unit-diagram.html 
title="Counter"
pcount = 6
pname1 = "input"
ptype1 = "comparator"
pname2 = "reset"
ptype2 = "comparator"
pname3 = "start"
ptype3 = "gainbias"
pname4 = "step"
ptype4 = "gainbias"
pname5 = "finish"
ptype5 = "gainbias"
pname6 = "gain"
ptype6 = "gainbias"
%}

## Overview

The Counter unit counts up (or down, depending on the **step** value) from a **start** value to a **finish** value.  A trigger at the input of the unit (i.e. coming from the left) will cause the step value to be added to the current output value of the unit.  If the resulting output value exceeds the **finish** value then depending on the **Wrap?** setting, the Counter's output value will either wrap back around to the **start** value, or, stop.  A trigger on the **reset** parameter will cause the output value to return to the **start** value.

Some applications are:
* Scanning (on tempo) through discrete sets such as slices, notes of a scale, clock divisions/multiplications, etc.
* Causing a threshold to be exceeded (and then something to happen) based on the count of another trigger source.

## Configuration

### Wrap?

* **yes**: Automatically reset to the start value once the output value reaches the **finish** value.  
* **no**: Stop at the finish value and wait for a manual reset.

### Process Rate

* **frame**: Process triggers and update the output value at the global frame rate (about 400Hz).
* **sample**: Process triggers and update the output value at the global sample rate (48kHz or 96kHz). This setting results in lower latency but requires more CPU.

## Parameters

### input
{% include comparator-control.html summary="Threshold controls for the input trigger." %}
A trigger at the unit input causes the counter to increment (or decrement) by the **step** value.

### reset
{% include comparator-control.html %}
A trigger received here causes the counter to return to the **start** value.

### start
{% include gainbias-control.html %}
The output value starts here and also returns to this value when the unit is reset.

### step
{% include gainbias-control.html %}
The amount by which the output value should change when a trigger is received at the (unit) input.

### finish
{% include gainbias-control.html %}
Depending on the **Wrap?** setting, the unit will count up to this value and stop or wrap around to the **start** value.

### gain
{% include gainbias-control.html %}
Scale the output by this amount.
