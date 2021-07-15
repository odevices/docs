---
layout: default
title: Signal Flow
parent: ER-301
---

# Signal Flow

All signals flow through the ER-301 at the same rate (48kHz or 96kHz, depending on the sample rate configuration in the system settings) and there is no difference between an audio signal or a modulation (aka CV) signal.  

Signal routing and processing in the ER-301 is handled according to the following 3 properties:

1. All signal processing (or producing) algorithms are encapsulated as [units](/er-301/units) protrayed as rectangles (w/ rounded edges) that take an (optional) input signal from the left and produce an output signal to the right.  
1. A [chain](/er-301/chains) is a sequence of zero or more [units](/er-301/units) where signal flows from left to right.  All chains have a source feeding the initial signal from the extreme left and and a sink that collects the final signal at the extreme right.
1. Each unit exposes its algorithm's parameters as [controls](/er-301/units/#control-types).  Depending on the design of the unit, each control may accept modulation (i.e. an input signal) from other (sub-)[chains](/er-301/chains).

In other words, signals propagate according to an inverted tree structure (see figure below), with signals starting at the leaves (i.e. sources), propagating along the branches (i.e. chains of units), combining inside units, and eventually reaching the root of the graph where the final signal either flows out to one of the output channels (OUT1-4), or as in the case of [global chains](/er-301/admin/globals), it becomes a signal source that can be tapped for use elsewhere. We can see how this recursive signal flow can extend as deep as necessary to implement your patch's needs.  The UI/UX takes advantage of this simple tree structure (as opposed to an arbitrary graph) to greatly simplify visualization and navigation.  However, in the rare cases where you need to break from the tree structure, you can by using something called [local connections](#local-connections).  This way simple patches stay easy while complex patches require just a little more fiddling with the UI.

{% include figure.html
  file="overview.png"
  caption="Chain of units process and feed signal to destinations such as the module's outputs or other units."
%}

**A concrete example:**
In the patch depicted below, an audio signal is tapped from external input IN2 and fed into a [Linear Bipolar VCA](/er-301/core-pkg/linear-bipolar-vca) unit.  The level control of the [Linear Bipolar VCA](/er-301/core-pkg/linear-bipolar-vca) unit is modulated by another (sub)chain which contains an [ADSR](/er-301/core-pkg/adsr) unit that is excited by a gate signal arriving at external input G4.  After the [Linear Bipolar VCA](/er-301/core-pkg/linear-bipolar-vca) unit, the signal is further processed by a [Ladder LPF](/er-301/core-pkg/ladder-lpf) (low pass filter) unit whose frequency control is modulated by a [Sine Osc](/er-301/core-pkg/sine-osc) unit.  The final output of this patch is routed to the output OUT3.

{% include figure.html
  file="example.png"
  caption="An example of how chains are used to route signals."
%}

## Local Connections