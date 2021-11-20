---
layout: draft-unit
title: Aliasing Saw
subtitle: A sawtooth oscillator.
parent: Core Package
grand_parent: ER-301
---

{% include gallery.html 
count=2
file1="aliasing-saw.png"
file2="aliasing-saw-f0-expanded.png"
%}

This unit is a full-featured sawtooth oscillator with inputs for both exponential and linear frequency moduleation (FM), phase modulation (PM), and amplitude modulation (AM). The linear FM supports thru-zero operation.

This oscillator is not anti-aliased.

{% include osc-controls.md %}

{% include osc-tips.md %}

## See also

* [Aliasing Triangle](aliasing-triangle)
* [Sine Osc](sine-osc)
* [Single Cycle](single-cycle)