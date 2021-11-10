---
layout: draft-unit
title: Rectify
subtitle: Converting bipolar signals to unipolar signals.
parent: Core Package
grand_parent: ER-301
---

## Overview

This unit takes a bipolar signal (i.e. a signal that has both negative and positive portions) and forces it to be either all positive or all negative.  There are 3 types of rectification available:

{% include figure.html
file="rectify.png"
%}

| **Type** | **Description** |
| positive half | Pass the positive portion of the input signal unaffected and clamp the negative portion to zero. |
| negative half | Pass the negative portion of the input signal unaffected and clamp the positive portion to zero. |
| full | Invert the negative portion so that it is positive.  Leave the positive portion unaffected. |

## Parameters

### type
{% include option-control.html %}
Here you choose among the 3 available rectification types.
