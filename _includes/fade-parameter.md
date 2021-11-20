### fade
{% include fader-control.html summary = "Fade time when looping or resetting the playback position." %}
The output might jump discontinuously when the play head loops at the beginning (ending) of the sample, or, when a trigger resets the play head position.  When this happens, a fade is used smooth over the discontinuity in the output thus suppressing pops.  This parameter sets the length of the fade used.

