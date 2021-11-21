---
layout: draft-unit
title: Envelope Follower
subtitle: Computes the slow-moving envelope of a fast-moving signal.
parent: Core Package
grand_parent: ER-301
---

{% include unit-diagram.html 
title="Envelope Follower"
pcount = 2
pname1 = "attack"
ptype1 = "gainbias"
pname2 = "release"
ptype2 = "gainbias"
%}

## Description

This unit smoothly traces the energy (i.e. amplitude) of the input signal while ignoring fast (typically audio-rate) changes.  First it rectifies the input signal so that negative portions are flipped to the positive side and then the result is fed through a special kind of low pass filter that has separate frequency cutoffs (i.e. decay rates) for the rising and falling portions of the signal.  The benefit of having separate frequency cutoffs is that the envelope can quickly react to onsets (percussive hits, for example) but still yield a nice smooth envelope as the sound dies out.

Some applications are:
* Extracting envelopes from audio.
* Slew limiting with separate rates for rising and falling portions of the signal.
* Filtering out triggers by how close they are to each other.

## Parameters

### attack
{% include gainbias-control.html %}

This sets the decay rate for rising portions of the rectified incoming signal.  Short decay rates will track the rectified signal very closely while longer decay rates will smooth out the abrupt changes.  Literally, this parameter sets how long it takes for the envelope to catch up to a signal who's amplitude is growing.


### release
{% include gainbias-control.html %}

This sets the decay rate for falling portions of the rectified incoming signal.  Short decay rates will track the rectified signal very closely while longer decay rates will smooth out the abrupt changes.  Literally, this parameter sets how long it takes for the envelope to catch up to a signal who's amplitude is shrinking.

## See also

* [Slew Limiter](slew-limiter)
* [ADSR](adsr)
* [Skewed Sine Env](skewed-sine-env)