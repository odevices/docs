---
layout: default
title: Raw Player
parent: Units
grand_parent: ER-301
---

## Applications

  - This is the cheapest (i.e. lightest on CPU) method for straight
    sample playback (when no re-pitching is required).
  - Playing back pre-recorded automations (triggers, gates, CV, etc.)

## Description

The Raw Player plays samples at the system rate (48kHz or 96kHz) with no
resampling or interpolation (i.e. it just plays the raw samples at 48kHz
for the 48kHz firmware and at 96kHz for the 96kHz firmware). This means
that only samples which are originally encoded at the system rate (48kHz
or 96kHz) will play at the correct pitch and speed. The benefit that
comes with this limitation is that samples can be played with minimal
CPU load. You can of course, use it to play back samples encoded at any
rate, they just won't be playing at their original pitch.

## Parameters