---
layout: default
title: CPU Load
parent: Admin
grand_parent: ER-301
nav_order: 6
---

You can query the CPU load at any time from the admin menu.

{% include gallery.html
count=2
file1="er-301/admin-maintenance.png"
file2="er-301/cpu-load.png"
%}

CPU load will ''usually'' be the sum of the fixed costs of all units in use (plus ~3% of overhead).  A unit’s cost does not depend on where you insert it except to the extent that mono vs stereo might affect it.  In general expect, a stereo unit's cost to be from 50% to 100% more than its mono version. The number of (local and global) connections does not matter.

# Exceptions 
In general, units are designed to have a fixed CPU cost that does not depend on their inputs. The cases where this is violated (in order of severity) are:

* Manual Grains: CPU load grows as more grains are overlapping (i.e. polyphony).  This happens when you trigger grain production faster and/or increase grain duration.
* All random-access sample playing units and delay units with a speed control: L1/L2 cache misses caused by non-sequential access to sample memory will result in increased CPU load (stalling). Layman translation: Randomly jumping around in the buffer at audio rates, or playback at really high speeds (>10x). This forces the ER-301 to repeatedly query the RAM (slow) for necessary data because it is not in the L1/L2 memory cache (fastest).

# Actual Measurements 
Forum user [a773](https://forum.orthogonaldevices.com/u/a773/summary) has compiled this listing of CPU load measurements for a selection of units:
[a773's Unit CPU Load measurements](https://docs.google.com/spreadsheets/d/13hDQcJRfDA45yTufJo0tFy8AQ1Spit78vMehDIb3y0o/edit?usp=sharing)
