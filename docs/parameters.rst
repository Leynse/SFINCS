Input parameters
=====

Different input parameters can be changed, see below.

Parameters
-----

advection = 0 % default, no advection on. Otherwise: 1 for 1D advection scheme for modelling in 1D OR 2 for 2D advection scheme for modelling in 2D.

alpha = 0.75 %default, CFl-condition reduction. Decrease for additional numerical stability, minimum value is 0.1 and maximum is 0.75.

huthresh = 0.05 %default, minimal flow depth limiter in meters.

theta = 0.9 %default, theta value in momentum equation, 0.9 should give sufficient smoothing.

zsini = 0 %default, initial water level in meters.

qinf = 0 %default, infiltration rate, specify in -m^3/s (negative sign for infiltration)!
