## V/oct
{% include pitch-control.html summary = "Transpose fundamental by an amount in cents." %}

This parameter is used to transpose the base frequency up or down via a pitch CV (i.e. a signal that is calibrated to 1V/oct, typically one of the inputs from the ABCD matrix). In other words,

$$\text{f} = \text{f0} * 2 ^{\frac{x}{1200}}$$

where 

* $$x$$ is the value of this control (in cents)
* $$f0$$ is the base frequency (set via the f0 control)
* $$f$$ is the final output frequency of the oscillator

For example, if the base frequency (f0) is set to 55Hz and this V/oct parameter is set to 2400¢, then the resulting frequency will be 220Hz or 2 octaves above 55Hz:

$$220\text{Hz} = 55\text{Hz} * 2 ^{\frac{2400}{1200}}$$

Modulating this parameter corresponds to exponential FM.


