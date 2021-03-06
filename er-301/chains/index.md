---
layout: draft
title: Chains
parent: ER-301
nav_order: 3
---

<details open markdown="block">
  <summary>
    Table of contents
  </summary>
  {: .text-delta }
1. TOC
{:toc}
</details>

# Overview

A chain is a sequence of [units](/er-301/units) with signal coming in to the chain via a source, flowing through the units and then leaving the chain via a sink.  All sinks have exactly one chain associated with them, making sinks and chains one-to-one.  

{% include figure.html
  file="overview.png"
  caption="Anatomy of a (stereo) chain."
%}

# Sink
A sink may be:
* one of the 4 outputs (OUT1-4).
* the control port of a unit (e.g. the speed control of a Sample Player unit).
* the source of another chain.

It is not required to assign a sink to a chain.  Instead, every sink is associated with its own chain already.  In fact, the name of a chain corresponds to the name of its sink because they are in fact synonymous.  This just reflects the fact that a sink can only be fed a signal from one chain at a time.  Contrast this to how sources can have their signals routed to as many destinations as necessary.

{% include gallery.html
  count=3
  file1="out12-chain.png"
  caption1="This stereo chain routes to the stereo channel group OUT1+OUT2."
  file2="sample-player-shift-chain.png"
  caption2="This mono chain routes to the 'shift' control of a Sample Player unit."
  file3="global-clock-chain.png"
  caption3="This mono chain routes to a user-created global source called 'clock'."
%}

{% include tip.html
  content="If you need to combine multiple signals to feed to a sink then you should use the Mixer unit."
%}

The name section of the chain UI (also referred to as the header) shows a menu (in the sub-display) when it is focused:

{% include figure.html
file="mono-chain-header.png"
caption="When the chain header is focused a menu of chain operations is shown in the sub-display."
%}

* **Clear**: Deletes all units in the chain.
* **Load**: Load a [chain preset](/er-301/persistence#chain-presets) from the SD card.
* **Save**: Save the current chain's state (source assignments and units) to a preset file on the SD card.

{% include tip.html
content="When viewing a chain and its contained units, pressing HOME will move the UI focus to either the focused unit's header, or if no unit is focused, to the chain's header.  This is usually faster than scrolling with the knob."
%}

# Source 
{% include figure.html
file="input-source-selection.png"
caption="Pressing the M button underneath a chain's source area brings you to this screen where you can select from external inputs, local sources, and global sources."
%}

A source may be:
* one of the 20 external inputs (G1-4, IN1-4, ABCD1-3).
* one of the signal-generating units (e.g. Sample Player, Sine Osc, and so on).
* the output of another chain (e.g. global or local chains).

You select a chain's source by using the source menu located in the header of a chain.  In the case of stereo chains, there will be separate source selection menus for each channel, left and right. Once entering the source selection screen, you are first presented with the 20 external inputs (plus a loop-back copy of the outputs OUT1-4).  To access the local or global sources, press the choose (S1) button to cycle among the 3 types of sources.  Scroll through the list with the knob and use the M1-6 buttons to first expand a section of sources and again to choose the desired source.

On the other hand, pressing clear (S3) will clear any existing source assignment from the focused channel.

# Inserting Units 
Units can be inserted at any position in a chain by placing the cursor at the desired location (such as the beginning/ending of the chain, or, between two units) and pressing the insert (S3) button.  This will bring you to the unit selection menu where you can choose from a growing collection of units:

* [Builtin Units](/er-301/builtins) (built into the firmware)
* [Core Package](/er-301/core-pkg) (provided by O\|D)
* [Teletype Package](/er-301/teletype-pkg) (provided by O\|D)
* [ER-301 hub](https://er301-hub.netlify.app/) (created by users)

{% include gallery.html
  count=3
  file1="insert-between.png"
  caption1="Placing the cursor in between units will reveal an insert button (S3), as well as a sub-display scope that shows the signal that is passing through here."
  file2="unit-selection.png"
  caption2="Pressing the insert button (S3), takes us to the unit selection screen where we can scroll through the available units with the knob and choose one to instantiate using its corresponding M button."
  file3="unit-selection-filtering.png"
  caption3="If you hold down one of the S buttons and turn the knob, you can change the filter operands and thus pare down the number of displayed units to a particular type."
%}

# Output Meters 
At the end of a chain is a level meter for each channel that displays the chain's final [RMS](https://en.wikipedia.org/wiki/Root_mean_square) signal level in decibels of full-scale ([dBFS](https://en.wikipedia.org/wiki/DBFS)).  The level meters display signal levels from -60dBFS to +12dBFS with a line indicating 0dBFS.  In the case that the chain is routed to an output (OUT1-4) than any signal over 0dBFS will be hard clipped by the DAC.

{% include tip.html
content="A Limiter unit at the end of an output chain is very useful for soft clipping a hot signal before it reaches the DAC (unless that is what you want)."
%}

{% include tip.html
content="Don't know what dB or dBFS means? Having a hard time getting a feel for -6dBFS in term of actual signal level?  Try this excellent [decibel calculator](http://www.sengpielaudio.com/calculator-db.htm)."
%}
