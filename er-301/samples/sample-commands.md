---
layout: default
title: Sample Commands
parent: Samples
grand_parent: ER-301
---

Only units that use samples have these commands.

## Select from Card

## Select from Pool

This will bring you to the Sample Pool screen where you can select a sample to assign to this unit.  If the desired sample has not been loaded to memory yet than you can load the sample from card into the Sample Pool and then select it.  See [[ER-301/Sample Pool|Sample Pool]] for a complete description.


## Detach Buffer

## Edit Buffer

This menu item will bring up the slicing interface.  Here you can insert and delete slices while navigating around the assigned sample.

## Address Mode

This setting determines how the slice parameter chooses (or maps to) actual slices.

* nearest: The slice parameter value is mapped linearly to a sample position in the sample buffer (0 - beginning, 1 - ending) and the slice closest to the chosen sample position is selected.
* index: The slice parameter is mapped linearly to a slice index (0 - first slice, 1 - last slice).  In other words, slices are evenly distributed between 0 and 1.
* 12TET: The slice parameter is interpreted as a V/oct signal and each semitone is mapped to a slice (1st semitone - 1st slice, 2nd semitone - 2nd slice, and so on).

## Stereo Routing

This setting controls how a stereo sample is rendered to a mono output.  

* left: Only output the left channel and ignore the right channel.
* both: Output the average of the left and right channels.
* right: Only output the right channel and ignore the left channel.

This menu item is only shown if the chain containing this unit is a mono chain.
