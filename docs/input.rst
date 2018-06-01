Input description
=======

Overview
----------------------


Grid
----------------------

SFINCS uses an equidistant recti-linear grid, grid sizes for x- an y-direction can be different. SFINCS can only be used in cartesian coordinates. 
See also Delft Dasboard (OET) for the generation of a grid.


Bathymetry
----------------------
A bathymetry is defined in sfincs.dep, depth is down.
%%%%%
% sfincs.dep
% zbx0y0 zbx1y0 
% zbx0y1 zbx1y1 
%%%%%

Mask-file
----------------------
SFINCS uses a masker file to distinguish boundary (value=2)/active (value=1)/non-active (value=0) points within the supplied grid.
The file is normally make with the OET script 'sfincs_make_mask.m', where by default a value of -2 m to MSL is used to distguish the cells.
%%%%%
% sfincs.msk
% mskx0y0 mskx1y0 
% mskx0y1 mskx1y1 
%%%%%

Geo-mask-file
----------------------
Additionally a geo-mask-file is made using OET script 'sfincs_make_geomask_file.m'

Water-level boundaries
----------------------
First specify the input locations.
%%%%%
% sfincs.bnd 
% xloc1 yloc1
% xloc2 yloc2  
%%%%%
Then specify the water level time-series.
%%%%%
% sfincs.bzs
% t0 zsloc1 zsloc2
% t1 zsloc1 zsloc2
%%%%%

Discharge points
----------------------
A simple implementation of discharge points is added to SFINCS, specify values in m^3/s. First specify the location.
%%%%%
% sfincs.src 
% xloc1 yloc1
% xloc2 yloc2  
%%%%%
And then specify the values
%%%%%
% sfincs.dis
% t0 disloc1 disloc2
% t1 disloc1 disloc2 
%%%%%




