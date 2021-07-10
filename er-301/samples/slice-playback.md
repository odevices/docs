---
layout: default
title: Slice Playback
parent: Samples
grand_parent: ER-301
---

{% include figure.html
file="er-301/core/play-head-behavior-no-slices-forward.png"
%}

{% include figure.html
file="er-301/core/play-head-behavior-no-slices-reverse.png"
%}

When a sample with no slices is loaded, the play head will just keep advancing and looping back to the beginning (or ending) when it reaches the end (or beginning) because there is nothing to  tell it otherwise. Triggering will cause the play head to jump back to the beginning/ending of the sample.  You can insert slices but they are not seen by the play head until you activate one (via triggering). You can trigger a sample player either by a gate signal into the trig parameter or manually by hitting the *fire* button that ORs your manually created gate with the incoming modulation signal.  Here is a mini-walkthrough that shows what I mean:

1. Load up a Varispeed Player and attach a sample with 5 slices.
1. Set Play Extent to **slice**, CV-to-Slice Mapping to **index**, and Slice Polarity to **symmetric**.
1. Make sure the bias of [speed](#speed) parameter is set to 1x.
1. Set the bias of the [slice](#slice) parameter to 0 and manually *fire* (i.e. S3) the [gate](#gate) parameter.  The 1st slice should play.
1. Set the bias of the [slice](#slice) parameter to 0.25 and manually *fire* the [gate](#gate) parameter.  The 2nd slice should play.
1. Set the bias of the [slice](#slice) parameter to 0.5 and manually *fire* the [gate](#gate) parameter.  The 3rd slice should play.
1. Set the bias of the [slice](#slice) parameter to 0.75 and manually *fire* the [gate](#gate) parameter.  The 4th slice should play.
1. Set the bias of the [slice](#slice) parameter to 1.0 and manually *fire* the [gate](#gate) parameter.  The 5th slice should play.

Once a slice is activated, the reset position becomes the active slice and the stop position becomes the next slice in the case of forward playback, and the previous slice in the case of reverse playback.

{% include figure.html
file="er-301/core/play-head-behavior-sliced-forward.png"
%}

{% include figure.html
file="er-301/core/play-head-behavior-sliced-reversed.png"
%}

In both the **no slices** and **sliced** case, if the [shift](#shift) parameter is non-zero then the reset position of the play head will be shifted by a time interval equal to the shift parameter's value.