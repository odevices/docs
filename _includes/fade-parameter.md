### fade
{% include fader-control.html %}
The output might jump discontinuously when the play head loops at the beginning (ending) of the sample, or, when a trigger resets the play head position.  When this happens, a fade is used smooth over the discontinuity in the output thus suppressing pops.  This parameter sets the length of the fade used.

{% include pitfall.html
content="If you are using a single cycle wave sample to recreate a wavetable oscillator then it is recommended that you set this parameter to zero."
%}
