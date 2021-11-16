### wet
{% include gainbias-control.html %}

This parameter affects the cross-fade between the input signal and the playback signal in the output.  A value of 1 (i.e. 100% wet) means you will only hear the contents of the buffer.  A value of 0 (i.e. 100% dry) means you will only hear the signal received at the unit's input.  However, the cross-fade curve is not linear but rather lifted to counteract the tendency for loudness to dip in the center of a linear cross-fade curve.  The actual cross-fade curve looks like this:

{% include figure.html 
file="cross-fade.png"
%}

