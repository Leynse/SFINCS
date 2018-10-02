Input description
=======

Overview
----------------------


Grid
----------------------

SFINCS uses a staggered equidistant recti-linear grid, grid sizes for x- a y-direction can be different. SFINCS can only be used in cartesian coordinates. 
See also Delft Dasboard (OET) for the generation of a grid. Specify x0/y0/rotation/dx/dy/mmax/nmax.


Bathymetry
----------------------

A bathymetry is defined in sfincs.dep, depth is down.

Depth-file
%%%%%

depfile - sfincs.dep

% zbx0y0 zbx1y0 %

% zbx0y1 zbx1y1 %


Mask-file
----------------------

SFINCS uses a masker file to distinguish boundary (value=2)/active (value=1)/non-active (value=0) points within the supplied grid.
The file is normally make with the OET script 'sfincs_make_mask.m', where by default a value of -2 m to MSL is used to distguish the cells.

%%%%%

mskfile = sfincs.msk

% mskx0y0 mskx1y0 %

% mskx0y1 mskx1y1 %


Geo-mask-file
----------------------

Additionally a geo-mask-file is made using OET script 'sfincs_make_geomask_file.m'

Water-level boundaries
----------------------

Boundary locations
%%%%%

First specify the input locations.

bndfile - sfincs.bnd 

% xloc1 yloc1 %

% xloc2 yloc2 %  

Time-series
%%%%%

Then specify the water level time-series.

bzsfile = sfincs.bzs

% t0 zsloc1 zsloc2 %

% t1 zsloc1 zsloc2 %

%%%%%

Discharge points
----------------------

A simple implementation of discharge points is added to SFINCS, specify values in m^3/s. First specify the location.

Location
%%%%%

srcfile = sfincs.src 

% xloc1 yloc1 %

% xloc2 yloc2 % 


Time-series
%%%%%

And then specify the values.

disfile = sfincs.dis

% t0 disloc1 disloc2 %

% t1 disloc1 disloc2 %

Wind and rain
----------------------

There are a few different options to specify wind and rain input. The first is to use a spatially varying spiderweb input (as in Delft3D) for only the wind input, or for the wind as well as the rain input. The second is to use a spatially varying grid input (as in Delft3D) for the u- and v-velocties and/or the rain input. At the last it is also possible to use a spatially uniform input for wind and rain, which is faster but also more simplified. For the wind input the drag coefficients are wind-speeds dependent, see below.

Spiderweb-input:
%%%%% 

spwfile = 'sfincs.spw'


Delft3D-meteo input:
%%%%%

Wind:

amufile = 'sfincs.amu'

amvfile = 'sfincs.amv'

Rain:

amprfile = 'sfincs.ampr'

Spatially-uniform wind input:
%%%%%
'vmag' is the wind speed in m/s, 'vdir' is the wind direction in nautical from where the wind is coming. The input format is the same as with Delft3D.

wndfile = 'sfincs.wnd'

% t0 vmag0 vdir0 %

% t1 vmag1 vdir1 %

Spatially-uniform rain input:
%%%%%

Rain input in mm/hr.

precipfile = 'sfincs.prcp'

% t0 prcp0 %

% t1 prcp1 %


Drag Coefficients: 
%%%%%

The drag coefficients are varying with wind speed and implemented as in Delft3D. The values are based on Vatvani et al. 2012. There is specified for how many points 'cd_nr' a velocity 'cd_wnd' and a drag coefficient 'cd_val' is specified, the following are the default values:

% cd_nr = 3 %

% cd_wnd = 0 28 50 %

% cd_val = 0.0010 0.0025 0.0015 %


Friction
----------------------

Friction is specified with a Manning roughness coefficient 'n' [s/m^{1/3}]. This can be done spatially uniform or spatially varying where a reference level in meters 'rgh_lev_land' is used to distinguish land 'manning_land' and sea 'manning_sea' with different friction values.

Spatially uniform:
%%%%%
manning = 0.04 (default)

Spatially varying:
%%%%%

% rgh_lev_land = 0 (default) %

% manning_land = -999 (default) %

% manning_Sea = -999 (default) %


