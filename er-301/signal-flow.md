---
layout: default
title: Signal Flow
parent: ER-301
nav_order: 2
---

<details open markdown="block">
  <summary>
    Table of contents
  </summary>
  {: .text-delta }
1. TOC
{:toc}
</details>

All signals flow through the ER-301 at the same rate (48kHz or 96kHz, depending on the sample rate configuration in the system settings) and there is no difference between an audio signal or a modulation (aka CV) signal.  As is natural for open-ended DSP environments like the ER-301, algorithms and their associated parameters are encapsulated into discrete blocks called units.  However, distinct from other open-ended environments (such as [Max](https://en.wikipedia.org/wiki/Max_(software)) or [Pd](https://en.wikipedia.org/wiki/Pure_Data)), I opted for a restricted form of signal routing in order to avoid the complications that arbitrary networks cause for UI design.  I believe that the ER-301's restricted style of signal routing has grown to be one of its core strengths.

# A Patching Language 
{% include figure.html
  file="er-301/signal-flow/overview.png"
  caption="Chain of units process and feed signal to destinations such as the module's outputs or other units."
%}
Signal routing and processing in the ER-301 are handled according to the following 3 rules:
* A **chain** is a sequence of zero or more **units** where signal flows from left to right.
* A **unit** encapsulates a signal processing algorithm and exposes the algorithm's parameters as **controls**.
* Unit **controls** are modulated by other **chains**.
In the following diagram, we can see how this recursive signal flow can extend as deeply as necessary to meet (most of) a patch's signal routing requirements.

**A concrete example:**
In the patch depicted below, an audio signal is tapped from external input IN2 and fed into a [Linear VCA](core-units/linear-vca) unit.  The level control of the [Linear VCA](core-units/linear-vca) unit is modulated by another (sub)chain which contains an [ADSR](core-units/adsr) unit that is excited by a gate signal arriving at external input G4.  After the [Linear VCA](core-units/linear-vca) unit, the signal is further processed by a [Ladder LPF](core-units/ladder-lpf) (low pass filter) unit whose frequency control is modulated by a [Sin Oscillator](core-units/sin-osc) unit.  The final output of this patch is routed to the output OUT3.

{% include figure.html
  file="er-301/signal-flow/example.png"
  caption="An example of how chains are used to route signals."
%}

# Chains 
A chain is a sequence of units with signal coming in to the chain via a source, flowing through the units and then leaving the chain via a sink.  All sinks have exactly one chain associated with them, making sinks and chains one-to-one.  

{% include figure.html
  file="er-301/chain-anatomy/overview.png"
  caption="Anatomy of a (stereo) chain."
%}

## Sink
A sink may be:
* one of the 4 outputs (OUT1-4).
* the control port of a unit (e.g. the speed control of a Sample Player unit).
* the source of another chain.

It is not required to assign a sink to a chain.  Instead, every sink is associated with its own chain already.  In fact, the name of a chain corresponds to the name of its sink because they are in fact synonymous.  This just reflects the fact that a sink can only be fed a signal from one chain at a time.  Contrast this to how sources can have their signals routed to as many destinations as necessary.

{% include gallery.html
  count=3
  file1="er-301/chain-anatomy/out12-chain.png"
  caption1="This stereo chain routes to the stereo channel group OUT1+OUT2."
  file2="er-301/chain-anatomy/sample-player-shift-chain.png"
  caption2="This mono chain routes to the 'shift' control of a Sample Player unit."
  file3="er-301/chain-anatomy/global-clock-chain.png"
  caption3="This mono chain routes to a user-created global source called 'clock'."
%}

{% include tip.html
  content="If you need to combine multiple signals to feed to a sink then you should use the Mixer unit."
%}

The name section of the chain UI (also referred to as the header) shows a menu (in the sub-display) when it is focused:

{% include figure.html
file="er-301/chain-anatomy/mono-chain-header.png"
caption="When the chain header is focused a menu of chain operations is shown in the sub-display."
%}

* **Clear**: Deletes all units in the chain.
* **Load**: Load a [chain preset](persistence#chain-presets) from the SD card.
* **Save**: Save the current chain's state (source assignments and units) to a preset file on the SD card.

{% include tip.html
content="When viewing a chain and its contained units, pressing HOME will move the UI focus to either the focused unit's header, or if no unit is focused, to the chain's header.  This is usually faster than scrolling with the knob."
%}

## Source 
{% include figure.html
file="er-301/chain-anatomy/input-source-selection.png"
caption="Pressing the M button underneath a chain's source area brings you to this screen where you can select from external inputs, local sources, and global sources."
%}

A source may be:
* one of the 20 external inputs (G1-4, IN1-4, ABCD1-3).
* one of the signal-generating units (e.g. Sample Player, Sine Osc, and so on).
* the output of another chain (e.g. global or local chains).

You select a chain's source by using the source menu located in the header of a chain.  In the case of stereo chains, there will be separate source selection menus for each channel, left and right. Once entering the source selection screen, you are first presented with the 20 external inputs (plus a loop-back copy of the outputs OUT1-4).  To access the local or global sources, press the choose (S1) button to cycle among the 3 types of sources.  Scroll through the list with the knob and use the M1-6 buttons to first expand a section of sources and again to choose the desired source.

On the other hand, pressing clear (S3) will clear any existing source assignment from the focused channel.

## Inserting Units 
Units can be inserted at any position in a chain by placing the cursor at the desired location (such as the beginning/ending of the chain, or, between two units) and pressing the insert (S3) button.  This will bring you to the unit selection menu where you can choose from a growing [library of units](core-units).

{% include gallery.html
  count=3
  file1="er-301/chain-anatomy/insert-between.png"
  caption1="Placing the cursor in between units will reveal an insert button (S3), as well as a sub-display scope that shows the signal that is passing through here."
  file2="er-301/chain-anatomy/unit-selection.png"
  caption2="Pressing the insert button (S3), takes us to the unit selection screen where we can scroll through the available units with the knob and choose one to instantiate using its corresponding M button."
  file3="er-301/chain-anatomy/unit-selection-filtering.png"
  caption3="If you hold down one of the S buttons and turn the knob, you can change the filter operands and thus pare down the number of displayed units to a particular type."
%}

## Output Meters 
At the end of a chain is a level meter for each channel that displays the chain's final [RMS](https://en.wikipedia.org/wiki/Root_mean_square) signal level in decibels of full-scale ([dBFS](https://en.wikipedia.org/wiki/DBFS)).  The level meters display signal levels from -60dBFS to +12dBFS with a line indicating 0dBFS.  In the case that the chain is routed to an output (OUT1-4) than any signal over 0dBFS will be hard clipped by the DAC.

{% include tip.html
content="A Limiter unit at the end of an output chain is very useful for soft clipping a hot signal before it reaches the DAC (unless that is what you want)."
%}

{% include tip.html
content="Don't know what dB or dBFS means? Having a hard time getting a feel for -6dBFS in term of actual signal level?  Try this excellent [decibel calculator](http://www.sengpielaudio.com/calculator-db.htm)."
%}

# Units 
{% include figure.html
file="er-301/unit-anatomy/unit-header.png"
caption="A unit's header menu contains commands for bypassing, re-init'ing, and deleting itself."
%}

{% include detail.html
content="For further details on available units, see the [library of units](core-units)."
%}

A unit encapsulates a signal processing algorithm and exposes it parameters as controls.  Signal enters a unit either from the left or via its control ports (from below).  Signal leaves a unit from the right.  Stereo chains will contain only stereo units, while mono chains will contain only mono units.

If you move the cursor over to any unit's header area (i.e. or press HOME while the cursor is inside a unit), the sub-display will switch to the unit's header menu containing 3 commands:

* **Bypass**: Re-route the chain's signal flow so that this unit is skipped.
* **Re-init**: Restore all unit parameters to their default values.
* **Delete**: Remove this unit from the chain.

## Bypassing 
{% include figure.html
file="er-301/unit-anatomy/bypassed-unit.png"
caption="This unit has been bypassed."
%}
Activating the Bypass command located in a unit's header menu will cause the unit's output to be disconnected from the next (non-bypassed) unit.  The next unit will instead get its input from the previous (non-bypassed) unit.

{% include figure.html
file="er-301/bypass.png"
caption="Units can be bypassed such that they still receive an input signal but their outputs are ignored."
%}

{% include pitfall.html
content="By default, a bypassed unit will still process its inputs and thus consume CPU cycles. The reason for this is to provide smoother transitions when un-bypassing a unit.  If you wish to have bypassed units completely disabled see the next section."
%}

## Disabling 
There is a setting in Admin>Settings that let's you choose whether bypassing a unit should also disable it.  In this context, "disabling a unit" means removing it from the DSP scheduler so that the unit no longer consumes CPU cycles.  Un-bypassing the unit will re-enable it.

{% include figure.html
file="er-301/unit-anatomy/bypass-disable-setting.png"
caption="Here is the relevant setting for changing the disable behavior of a bypassed unit."
%}

# Controls 
Most units have controls that allow you to alter the parameters of its algorithm.  Various types of controls are needed to handle the wide variety of of algorithmic parameters as well as their various ranges and quantities (e.g. frequency, time, gain, pitch, and so on).  

## Gain/Bias 
This is the most common and most versatile control type.  It is essentially a modulation source plus controls for attenuation (gain) and offset (bias).

$$\text{value} = \text{gain} * \text{modulation} + \text{bias}$$

As its name implies, the final value of the parameter is derived by multiplying any incoming modulation by a gain and then adding a bias.  If there is no modulation then the value of the parameter is just the bias. When you first select this control (with the M button underneath it), the knob will be focused to and controlling the bias parameter.  You can use the S2 and S3 buttons to switch between adjusting the gain and bias parameters, respectively.  To dive down into the modulation sub-chain, press S1. Pressing UP will deselect this control and restore focus to the chain.

The quantity, range and units of the bias value will depend on the actual parameter.  Refer to the documentation for each unit for these details.

{% include gallery.html
  count=3
  file1="er-301/unit-anatomy/gainbias.png"
  caption1="An example of a Gain/Bias control is the speed parameter of the Sample Player unit."
  file2="er-301/unit-anatomy/gain-bias-fader.png"
  caption2="The Gain/Bias control shows the bias value on the left fader and the final value (or its range if changing quickly) on the right fader."
  file3="er-301/unit-anatomy/gain-bias-sub-display.png"
  caption3="The sub display gives access to the modulation sub-chain and provides a mini-scope view of the signal that is being fed to this control."
%}

{% include tip.html
content="You can quickly zero a focused parameter by pressing ZERO (Shift+HOME).  You can also quickly restore a parameter to the value it had when you focused it by pressing the CANCEL button."
%}

## Pitch 
This control is used whenever we want to utilize a V/oct signal to sequence a unit's pitch (or pitch-like) parameter.  There is no gain because scaling a V/oct signal would destroy the volt-per-octave relationship.  However, you can transpose the incoming modulation up or down in [cents (¢)](https://en.wikipedia.org/wiki/Cent_(music)).

$$\text{value} = 10*\text{modulation} + \frac{\text{transpose}}{1200}$$

Why 10?  This is the gain necessary to convert the internal signal range back to a voltage.  Recall that the ABCDx inputs accept inputs from -10V to 10V and that signals in this range are digitized and mapped to the interval between -1 and 1.  Multiplying by 10.24 essentially undoes this mapping so that we can operate on the voltages necessary for V/oct calculation.

{% include gallery.html
  count=3
  file1="er-301/unit-anatomy/pitch.png"
  caption1="An example of a pitch control is the V/oct parameter on the Sample Player unit."
  file2="er-301/unit-anatomy/pitch-fader.png"
  caption2="The Pitch control shows the transpose amount on the left fader and the actual resulting pitch (or its range if changing quickly) on the right fader."
  file3="er-301/unit-anatomy/pitch-sub-display.png"
  caption3="The sub display gives access to the modulation sub-chain and provides a mini-scope view of the signal that is being fed to this control."
%}

{% include pitfall.html
content="Accurate V/oct tracking is only possible with the calibrated [ABCDx inputs](front-panel#abcdx-input-matrix)"
%}

## Threshold 
This control changes its digital output (high/low, on/off) every time the incoming modulation crosses an adjustable threshold from below.  Focusing this control (via an M button) and then pressing S2 will allow you to adjust the threshold.  The S3 button will manually 'fire' additional gates into the unit.  There are 3 ways that the digital output is derived from the input signal:

* **trigger**: Positive going edges cause instantaneous (single sample) trigger events.
* **gate**: The parameter is ON only while the incoming signal exceeds the threshold.
* **latch**: If OFF, a positive going edge cause the parameter to turn ON.  If ON, a positive going edge cause the parameter to turn OFF.

Refer to the individual unit documentation for details on which behavior is configured for each unit control.

{% include gallery.html
  count=3
  file1="er-301/unit-anatomy/trigger.png"
  caption1="An example of the Threshold control is the trig parameter of the Sample Player unit."
  file2="er-301/unit-anatomy/trigger-main-display.png"
  caption2="The Threshold control's circular display pulses whenever the incoming signal crosses the threshold."
  file3="er-301/unit-anatomy/trigger-sub-display.png"
  caption3="The sub display gives access to the modulation sub-chain and provides a mini-scope view of the signal that is being fed to this control."
%}

## Simple Fader 
This control is used when modulation is not needed.  It is designed for set-and-forget type parameters.  When this kind of control is highlighted the sub-display will show a scope that portrays the output signal of the unit.

{% include figure.html
  file="er-301/unit-anatomy/fader.png"
  caption="An example of the simple fader control is the fade parameter of the Sample Player unit."
%}

## Option 
This control is used to select an option from a list of choices.

{% include figure.html
  file="er-301/unit-anatomy/option.png"
  caption="An example of the option control is the type parameter of the Limiter unit."
%}

