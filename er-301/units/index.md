---
layout: draft
title: Units
parent: ER-301
has_children: true
nav_order: 4
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

A unit encapsulates a signal processing algorithm and exposes it parameters as controls.  Signal enters a unit either from the left or via its control ports (from below).  A unit outputs the final signal to the right.  Stereo chains will contain only stereo units, while mono chains will contain only mono units.

{% include figure.html
file="unit-header.png"
caption="A unit's header menu contains commands for bypassing, re-init'ing, and deleting itself."
%}

If you move the cursor over to any unit's header area (i.e. or press HOME while the cursor is inside a unit), the sub-display will switch to the unit's header menu containing 3 commands:

* **Bypass**: Re-route the chain's signal flow so that this unit is skipped.
* **Re-init**: Restore all unit parameters to their default values.
* **Delete**: Remove this unit from the chain.

# Commands

All units have these commands.

## Rename

## Load

## Save

## Bypass

{% include figure.html
file="bypassed-unit.png"
caption="This unit has been bypassed."
%}
Activating the Bypass command located in a unit's header menu will cause the unit's output to be disconnected from the next (non-bypassed) unit.  The next unit will instead get its input from the previous (non-bypassed) unit.

{% include figure.html
file="bypass.png"
caption="Units can be bypassed such that they still receive an input signal but their outputs are ignored."
%}

{% include pitfall.html
content="By default, a bypassed unit will still process its inputs and thus consume CPU cycles. The reason for this is to provide smoother transitions when un-bypassing a unit.  If you wish to have bypassed units completely disabled see the next section."
%}

### Disable when bypassed 
There is a setting in Admin>Settings that let's you choose whether bypassing a unit should also disable it.  In this context, "disabling a unit" means removing it from the DSP scheduler so that the unit no longer consumes CPU cycles.  Un-bypassing the unit will re-enable it.

{% include figure.html
file="bypass-disable-setting.png"
caption="Here is the relevant setting for changing the disable behavior of a bypassed unit."
%}


## Delete

## Config

## Collapse

## Expand

## Edit Controls

# Control Types
Most units have controls that allow you to alter the parameters of its algorithm.  Various types of controls are needed to handle the wide variety of of algorithmic parameters as well as their various ranges and quantities (e.g. frequency, time, gain, pitch, and so on).  

## Gain/Bias 
This is the most common control type.  You will already be very familiar with its operation because it is often used on modules in real life as a CV input jack combined with attenuverter and an offset knobs.  In the case of the ER-301, the CV input corresponds to the signal coming from this control's modulation sub-chain, while the attenuverter is renamed as **gain** and the offset is renamed as **bias**.  The effect of gain and bias on the input modulation can be succinctly described as follows:

$$\text{final value} = \text{gain} * \text{modulation} + \text{bias}$$

If there is no modulation (i.e. an empty sub-chain outputs a constant zero value), or the gain is set to zero, then the value of the parameter is just the bias just like on a real-life module. When you first select this control (with the Mx button underneath it), the knob will be focused to on the bias parameter.  You can use the S2 and S3 buttons to switch between adjusting the gain and bias parameters, respectively.  To dive down into the modulation sub-chain, press S1. Pressing UP will deselect this control and restore focus to the chain.

The quantity, range, and units of the bias value will depend on the actual parameter.  Refer to the documentation for each unit for these details.

{% include gallery.html
  count=3
  file1="gainbias.png"
  caption1="An example of a Gain/Bias control is the speed parameter of the Sample Player unit."
  file2="gain-bias-fader.png"
  caption2="The Gain/Bias control shows the bias value on the left fader and the final value (or its range if changing quickly) on the right fader."
  file3="gain-bias-sub-display.png"
  caption3="The sub display gives access to the modulation sub-chain and provides a mini-scope view of the signal that is being fed to this control."
%}

{% include tip.html
content="You can quickly zero a focused parameter by pressing ZERO (Shift+HOME).  You can also quickly restore a parameter to the value it had when you focused it by pressing the CANCEL button."
%}

## Pitch 
This offset-only control is used whenever we want to utilize a V/oct signal to sequence a unit's pitch (or pitch-like) parameter.  There is no gain because scaling a V/oct signal would destroy the volt-per-octave relationship.  However, you can transpose the incoming modulation up or down in [cents (¢)](https://en.wikipedia.org/wiki/Cent_(music)).

$$\text{value} = 10*\text{modulation} + \frac{\text{transpose}}{1200}$$

Why 10?  This is the gain necessary to convert the internal signal range back to a voltage.  Recall that the ABCDx inputs accept inputs from -10V to 10V and that signals in this range are digitized and mapped to the interval between -1 and 1.  Multiplying by 10.24 essentially undoes this mapping so that we can operate on the voltages necessary for V/oct calculation.

{% include gallery.html
  count=3
  file1="pitch.png"
  caption1="An example of a pitch control is the V/oct parameter on the Sample Player unit."
  file2="pitch-fader.png"
  caption2="The Pitch control shows the transpose amount on the left fader and the actual resulting pitch (or its range if changing quickly) on the right fader."
  file3="pitch-sub-display.png"
  caption3="The sub display gives access to the modulation sub-chain and provides a mini-scope view of the signal that is being fed to this control."
%}

{% include pitfall.html
content="Accurate V/oct tracking is only possible with the calibrated [ABCDx inputs](/er-301/front-panel#abcdx-input-matrix)"
%}

## Comparator
This control changes its digital output (high/low, on/off) every time the incoming modulation crosses an adjustable threshold from below.  Focusing this control (via an M button) and then pressing S2 will allow you to adjust the threshold.  The S3 button will manually 'fire' additional gates into the unit.  There are 3 ways that the digital output is derived from the input signal:

* **trigger**: Positive going edges cause instantaneous (single sample) trigger events.
* **gate**: The parameter is ON only while the incoming signal exceeds the threshold.
* **latch**: If OFF, a positive going edge cause the parameter to turn ON.  If ON, a positive going edge cause the parameter to turn OFF.

Refer to the individual unit documentation for details on which behavior is configured for each unit control.

{% include gallery.html
  count=3
  file1="trigger.png"
  caption1="An example of the Comparator control is the trig parameter of the Sample Player unit."
  file2="trigger-main-display.png"
  caption2="The Comparator control's circular display pulses whenever the incoming signal crosses the threshold."
  file3="trigger-sub-display.png"
  caption3="The sub display gives access to the modulation sub-chain and provides a mini-scope view of the signal that is being fed to this control."
%}

## Simple Fader 
This control is used when modulation is not needed.  It is designed for set-and-forget type parameters.  When this kind of control is highlighted the sub-display will show a scope that portrays the output signal of the unit.

{% include figure.html
  file="fader.png"
  caption="An example of the simple fader control is the fade parameter of the Sample Player unit."
%}

## Option 
This control is used to select an option from a list of choices.

{% include figure.html
  file="option.png"
  caption="An example of the option control is the type parameter of the Limiter unit."
%}

