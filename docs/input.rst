Input description
=======

Overview
----------------------

The input for SFINCS is supplied using various text-files, which are linked through the main input file: sfincs.inp.
Below an example is given of this file, which uses a keyword/value layout. 
Within this section of the input description all major input settings and files are discussed.
For more information regarding specific parameters see the pages 'Input parameters' or 'Output parameters'.
The required input files can also be made using the model maker of SFINCS in Delft Dashboard (https://publicwiki.deltares.nl/display/DDB/Delft+Dashboard),
or using Matlab scripts from the OpenEarthTools (OET, https://svn.oss.deltares.nl/repos/openearthtools/trunk/matlab/applications/DelftDashBoard/general/sfincs/).

**sfincs.inp**

.. code-block:: text

	x0              = 0
	y0              = 0	
	mmax            = 100
	nmax            = 100
	dx              = 100
	dy              = 100
	rotation        = 0
	
	depfile         = sfincs.dep
	mskfile         = sfincs.msk
	geomskfile	= sfincs.gms
	indexfile       = sfincs.ind

	bndfile        = sfincs.bnd
	bzsfile        = sfincs.bzs
	spwfile        = sfincs.spw
	amprfile       = sfincs.ampr

	advection	= 0
	alpha           = 0.75
	huthresh	= 0.05
	manning         = 0.04	
	theta 		= 0.9
	qinf            = 0.0

	tref            = 20180000 000000
	tstart          = 20180000 000000
	tstop           = 20180001 000000
	
	dtout           = 3600
	dthisout        = 600

	inputformat     = bin
	outputformat    = bin
	
	zsfile          = zs.dat
	hmaxfile        = hmax.dat
	hmaxgeofile     = hmaxgeo.dat	
	
	obsfile         = sfincs.obs
	

Grid & bathymetry
----------------------

Grid
SFINCS uses a staggered equidistant recti-linear grid, grid sizes for x- a y-direction can be different. SFINCS can only be used in cartesian coordinates. 
The grid is initialised by stating an origin location (x0, y0), a number of grid cells in x-&y-direction (mmax, nmax) and the grid sizes in x-&y-direction (dx,dy).
If desired the grid can also be rotated using 'rotation', in degrees from the x-axis (east) in anti-clockwise direction.


Depth-file
%%%%%
A bathymetry is defined in sfincs.dep based on the specified grid, depth is down.


**depfile = sfincs.dep**

.. code-block:: text

	<zb x0,y0> <zb x1,y0> 

	<zb x0,y1> <zb x1,y1>

	

Mask-file
%%%%%

SFINCS uses a masker file to distinguish boundary (value=2)/active (value=1)/non-active (value=0) cells within the supplied grid.
If boundary water levels are supplied, these are only forced to the cells with a value of 2. 
Cells with a value of 0 are inactive and no fluxes from/to these cells are calculated.
The file can be made with the OET script 'sfincs_make_mask.m', whereby default a value of -2 m to MSL is used to distinguish the cells.

**mskfile = sfincs.msk**

.. code-block:: text

	<msk (x0,y0)> <msk (x1,y0)>

	<msk (x0,y1)> <msk (x1,y1)>


Geo-mask & index file
%%%%%

Additionally a geo-mask & index file can  made using OET script 'sfincs_make_geomask_file.m', these files are needed when converting the model output the google earth kml-files when post-processing.

**keywords**

.. code-block:: text

	geomskfile	= sfincs.gms
	indexfile       = sfincs.ind

Input format bathymetry
%%%%%

The depth/mask/geomask/index-files can be binary or ASCII files. 
For the former specify 'inputformat = bin' (default), for the latter specify 'inputformat = asc'.


External forcing
----------------------

Different types of external forcing can be supplied within SFINCS.
Discussed are the water-level boundaries, discharge points, wind & rain and waves.


Water-level boundaries
%%%%%

To specify water-level time-series to the boundary cells (msk=2), first the input locations have to be specified in 'sfincs.bnd'.
For every boundary point there is interpolated with a weighted average between the two closest input locations.


**bndfile - sfincs.bnd**

.. code-block:: text

	<bnd1 x1> <bnd1 y1>  
	
	<bnd2 x2> <bnd2 y2>  


Then in the file 'sfincs.bzs' the water level time-series are specified per input location.

**bzsfile = sfincs.bzs**

.. code-block:: text

	<time 1> <zs1 bnd1> <zs1 bnd2>

	<time 2> <zs2 bnd1> <zs2 bnd2>


Discharge points
%%%%%

A simple implementation of discharge points is added to SFINCS, specify values in m^3/s. 
First specify the locations in 'sfincs.src'.


**srcfile = sfincs.src**


.. code-block:: text

	<src1 x1> <src1 y1>  
	
	<src2 x2> <src2 y2>  



Then in the file 'sfincs.dis' the discharge time-series are specified per input location.

**disfile = sfincs.dis**

.. code-block:: text
	
	<time 1> <dis1 src1> <dis1 src2>

	<time 2> <dis2 src1> <dis2 src2>


Wind and rain
%%%%%

There are a few different options to specify wind and rain input: 

1) Use a spatially varying spiderweb input (as in Delft3D) for only the wind input, or for the wind as well as the rain input. 

2) Use a spatially varying grid input (as in Delft3D) for u- and v-velocities and/or the rain input. 

3) Use a spatially uniform input for wind and rain, which is faster but also more simplified.

4) Make a combination, for instance use a spiderweb for the wind input and a spatially uniform rain-input. When combining, test whether the forcing is as wanted since not all combinations might be possible.




**Spiderweb-input:**

spwfile = sfincs.spw


**Delft3D-meteo input:**

Wind:

amufile = sfincs.amu

amvfile = sfincs.amv

Rain:

amprfile = sfincs.ampr


**Spatially-uniform wind input:**

'vmag' is the wind speed in m/s, 'vdir' is the wind direction in nautical from where the wind is coming. The input format is the same as with Delft3D.


**wndfile = sfincs.wnd**

.. code-block:: text

	<time 1> <vmag1> <vdir1>

	<time 2> <vmag2> <vdir2>


**Spatially-uniform rain input:**


Rain input in mm/hr.

**precipfile = sfincs.prcp**

.. code-block:: text

	<time 1> <prcp0>

	<time 2> <prcp1>


**Drag Coefficients:**
For the wind input, the drag coefficients are wind-speeds dependent, see below.


The drag coefficients are varying with wind speed and implemented as in Delft3D. 
The default values are based on Vatvani et al. (2012). 
There is specified for how many points 'cd_nr' a velocity 'cd_wnd' and a drag coefficient 'cd_val' is specified, the following are the default values:

.. code-block:: text

	cd_nr = 3 

	cd_wnd = 0 28 50 

	cd_val = 0.0010 0.0025 0.0015 


Waves
%%%%%

The input of waves as boundary conditions is still work in progress. Right now the following input files should not be used:

.. code-block:: text

	bwvfile = ''

	bhsfile = ''

	btpfile = ''

	cstfile = ''

A varying time-series can for now be forced using the previously mentioned water level input 'sfincs.bzs'.


Friction
----------------------

Friction is specified with a Manning roughness coefficient 'n' [s/m^{1/3}] and can be done spatially uniform or spatially varying.


Spatially uniform:
%%%%%

Specify the keyword:

manning = 0.04 (default)

Spatially varying:
%%%%%

For spatially varying a reference level in meters 'rgh_lev_land' is used to distinguish land 'manning_land' (depth>rgh_lev_land) and sea 'manning_sea' (depth<rgh_lev_land) with different friction values.

.. code-block:: text

	rgh_lev_land = 0 (default) 

	manning_land = -999 (default) 

	manning_Sea = -999 (default) 


Time management
----------------------
The required model runtime can be specified by setting a reference date (tref), start date (tstart) and stop date (tstop). 
The format is 'yyyymmdd HHMMSS', see below

.. code-block:: text

	tref 	= yyyymmdd HHMMSS
	tstart 	= yyyymmdd HHMMSS
	tstop 	= yyyymmdd HHMMSS

Also the output date inverval can be controlled.
For the map output there is data output every 'dtout' seconds, for optional observation points this is 'dthisout' seconds.
When using a spiderweb-file for the wind input, the values are updated every 'dtwnd' seconds.

.. code-block:: text

	dtout 		= 600
	dthisout 	= 600
	dtwnd 		= 1800


Model output
----------------------

Output format
%%%%%

The main map output can be binary or ASCII files. 
For the former specify 'outputformat = bin' (default), for the latter specify 'outputformat = asc'.

Output files
%%%%%

**keywords*

.. code-block:: text
	hmaxfile 	= hmax.dat
	hmaxgeofile 	= hmaxgeo.dat
	zsfile 		= zs.dat
	vmaxfile 	= vmax.dat

Observation points
%%%%%

Observation points with water depth and water level output can be specified.
Per observation point the x-and y- coordinates are stated.

**obsfile = sfincs.obs**

.. code-block:: text

	<obs1 x1> <obs1 y1>  
	
	<obs2 x2> <obs2 y2>  

