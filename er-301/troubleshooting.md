---
layout: default
title: Troubleshooting
parent: ER-301
nav_order: 11
---

<details open markdown="block">
  <summary>
    Table of contents
  </summary>
  {: .text-delta }
1. TOC
{:toc}
</details>

# Troubleshooting 

## I hear clicks in the audio 

Most likely CPU usage is spiking over 95% but too briefly to show on the CPU load screen. The CPU load screen samples the load once per second so it can easily miss short spikes in CPU usage. I've tried to build all units so that their CPU usage is as constant as possible, but there are exceptions such as Manual Grains. That unit's CPU usage will depend on the number of simultaneous grains playing at any particular moment (from 0 to 16) which will depend on the interaction of grain duration and grain triggering.

## My ER-301 keeps rebooting repeatedly 

A reboot loop means that your PSU is not providing enough [power](power) to your ER-301.

## I hear hum or digital noise 

Modular power is not the cleanest.  The average modular case will have a noise floor of about -90dB.  You can do better but it takes work, money, and know-how.  Another (very common) reason you might hear noise on the ER-301 outputs is improper gain staging.  Modular outputs do not need amplification, in fact they should be attenuated!  For example, if you are recording the output of the ER-301 then you should set the input gain that uses the entire output range of the ER-301 like this:

1. Play a 1kHz full-scale sine wave from an output of the ER-301.  Full-scale means that it swings from -1 to 1 without clipping.
1. Plug this output of the ER-301 directly into a LINE input of your audio interface.  Make sure any settings like Hi-Z or "instrument gain" are disabled.  
1. Set the input gain of your audio interface such that the sine wave from the ER-301 just about clips and reduce about 2dB from that point.

This procedure insures that you are using the full range of both your ER-301 and your audio interface thereby giving you the lowest noise floor possible.  You should never touch this input gain when recording.  If you need more gain (say for example you are playing a very quiet sound from the ER-301) then apply the gain INSIDE the ER-301 not after it.  In general, amplification of quiet sounds should be applied as closely to their source as possible NOT at the final stage.

## My ER-301 keeps crashing 

If you experience a crash with the latest stable firmware release then please make a bug report on the forum providing as much detail as possible including the steps required to make the crash happen again.

If you experience a crash using the a pre-release firmware first make sure you are running the latest version as regular updates are made that resolve these errors. If the crash keeps happening even though you are using the latest firmware please make a bug report on the current firmware release thread.

## The knob is not working 

Did the set screw that secures the knob onto the encoder shaft become loose?  Check with an allen key wrench.

## Sudden reboot when I touch the knob (and I live in a dry area)

Static electricity is building up on your body somehow, so when you touch the metallic knob on the ER-301, the resulting discharge disrupts the internal power regulator causing a reboot.  The solution is described in [this post on the forum](https://forum.orthogonaldevices.com/t/sudden-restart-of-module/1429/25?u=odevices).
