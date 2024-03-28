+++
title="Circuits!"
date=2024-03-04
+++

# Linear continuous-time filters

In _signal processing_, a _filter_ is a device that removes unwanted components from a signal.
This means removing some frequency bands.

The word _filter_ is synonymous with the linear continuous-time filter.
This is a filter designed to remove certain frequencies and allow others to pass.
They are approximately linear in response so the output signal does not contain frequency components not present in the input.

The **frequency response** of a filter can be classified into a number of different _bandforms_.
The "bandform" refers to which frequency bands the filter allows through (the _passband_) and which are rejected (the _stopband_).
Bandforms include:

- "Low-pass": low frequencies passed, high frequencies attenuated
- "High-pass": high frequences passed, low frequencies attenuated
- "Band-pass": only frequencies in the specified band are passed
- "Band-stop": only frequencies in the specified band are attenuated
- "Notch": rejects just one specific frequency
- "Comb filter": Has multiple regularly spaced, narrow passbands
- "All-pass filter": all frequencies are passed but with modified output phase

## Frequency domain

The most obvious characteristic of a filter is its gain versus frequency.
The _passband_ is the region of frequencies that are relatively unattenuated by the filter.
Most often it is considered to extend to the -3dB point.
The cutoff frequency, $f_c$, is the end of the passband.

The response then drops through a transition region (skirt) to a stopband, the region of significant attenuation.
This may be defined by some minimum atttenuation, like 40dB.

The other parameter of importance in the frequency domain is the _phase shift_ of the output signal relative to the input.
This is the complex response to the filter, $H(s)$, $s=j\omega$.

Phase is important because a signal entirely within the passband of a filter will emerge with its waveform distorted if the time delay of different frequencies in going through the filter is not constant.

Constant time-delay corresponds to a phase shift increasing linearly with frequency $\Delta t = -\frac{\phi}{d\omega} = -\frac{1}{2\pi}\frac{d\phi}{df}$.
The term _linear-phase filter_ is applied to a filter ideal in this respect.


## Time-domain 

Filters can be described in terms of their _time domain properties_:

- rise time (time to go from 10% to 90% of final value)
- overshoot
- delay time (time duration from input step to output reaching 50% of final value)
- ringing
- settling time (time to get within some specified amount of the final value and **stay there**)

Phase-shifting characteristics of filters imply a corresponding time delay, which may be seen plotted under the caption "group delay" versus frequency.

> _Attenuation_ refers to the loss of power of a signal without distorting its waveform.
> In this context, it refers to the gain of the filter.




> Phase-shift characteristics are important, because they determine the filter's in-band waveform distortion.


## Ideal brick-wall lowpass filter



## Laplace

### Really

## Yes

# Hi
