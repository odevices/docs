---
layout: unit
title: Single Cycle
parent: Core Package
grand_parent: ER-301
---

{% include figure.html
file="er-301/core/single-cycle.png"
%}

Takes any sliced sample and turns it into a interpolating wavetable oscillator.  Each slice is interpreted as containing one cycle of a waveform.

{% include tip.html
content="Often you might have a library of waveforms where each waveform is stored in its own WAV file.  You can easily load a selection of these waveform files into this unit as a [Sample Chain](/er-301/sample-chains)."
%}

{% include osc-controls.md %}

## Special Controls

### scan
{% include gainbias-control.html %}

Selects which waveshape (i.e. slice) to render from the wavetable.  If scanning between adjacent waveshapes then the wave produced is a linear interpolation of neighboring waveshapes.

{% include sample-commands.md %}