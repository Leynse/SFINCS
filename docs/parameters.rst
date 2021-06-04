Input parameters
=====

Different parameters for model input and output of SFINCS can be changed in **sfincs.inp**, see below. 

Traditionally SFINCS neglects the advection term in the SFINCS-LIE version ('advection = 0'). 
For super-critical flow conditions or modelling waves, the SFINCS-SSWE version can be used ('advection = 1' for 1D modelling and 'advection = 2' for 2D modelling) for better performance.        
     
Parameters for model input
-----
	mmax
	  :description:		Number of grid cells in x-direction
	  :units:		-
	  :default:		0
	  :min:			1
	  :max:			Inf (recommended is to limit the total number of active cells to 5 million)
	nmax
	  :description:		Number of grid cells in y-direction
	  :units:		-
	  :default:		0
	  :min:			1
	  :max:			Inf (recommended is to limit the total number of active cells to 5 million)	  
	dx
	  :description:		Grid size in x-direction
	  :units:		m
	  :default:		0
	  :min:			1.0e-3
	  :max:			Inf (recommended is a maximum grid size of 1000 meters)
	dy
	  :description:		Grid size in y-direction
	  :units:		m
	  :default:		0
	  :min:			1.0e-3
	  :max:			Inf (recommended is a maximum grid size of 1000 meters)	  
	x0
	  :description:		X-coordinate of first grid cell corner (1,1), thus not center of grid cell, in projected UTM zone.
	  :units:		m
	  :default:		0
	  :min:			0
	  :max:			Inf 
	y0
	  :description:		Y-coordinate of first grid cell corner (1,1), thus not center of grid cell, in projected UTM zone.
	  :units:		m
	  :default:		0
	  :min:			0
	  :max:			Inf 	  
	rotation
	  :description:		Rotation of the grid in degrees from the x-axis (east) in anti-clockwise direction
	  :units:		degrees
	  :default:		0
	  :min:			0
	  :max:			359.999 	  
	advection
	  :description:		setting for advection. 0 for no advection scheme (SFINCS-LIE), 1 for 1D advection scheme for modelling in 1D OR 2 for 2D advection scheme for modelling in 2D (SFINCS-SSWE).
	  :units:		-
	  :default:		0
	  :min:			0
	  :max:			2
	alpha	
	  :description:		CFL-condition reduction. Decrease for additional numerical stability, minimum value is 0.1 and maximum is 0.75.
	  :units:		-	
	  :default:		0.75		
	  :min:			0.1 (recommended)	
	  :max:			0.75 (recommended)		  
	huthresh	
	  :description:		Minimum flow depth limiter.
	  :units:		m
	  :default:		0.05
	  :min:			0.001 (recommended)
	  :max:			0.2 (recommended)
	theta
	  :description:		Smoothing factor in momentum equation. Advised not too change and to use 0.9 for regular SFINCS and 0.95 for subgrid version of SFINCS.
	  :units:		-
	  :default:		0.9
	  :min:			0.8
	  :max:			0.99
	zsini
	  :description:		Initial water level.
	  :units:		m above reference level
	  :default:		0
	  :min:			-Inf
	  :max:			Inf
	qinf
	  :description:		Infiltration rate, specify in +mm/hr.
	  :units:		mm/hr
	  :default:		0
	  :min:			0
	  :max:			Inf  
	manning
	  :description:		Uniform manning roughness, specify in s/m^(1/3).
	  :units:		s/m^(1/3)
	  :default:		0.04
	  :min:			0
	  :max:			Inf  	
	rgh_level_land
	  :description:		Elevation level to distinguish land and sea roughness (when using 'manning_land' and 'manning_sea').
	  :units:		m above reference level
	  :default:		0
	  :min:			-Inf
	  :max:			Inf  		  
	manning_land
	  :description:		Varying manning roughness based on elevation (above 'rgh_level_land', overules uniform 'manning', specify in s/m^(1/3).
	  :units:		s/m^(1/3)
	  :default:		-999 (=not used)
	  :min:			0
	  :max:			Inf  		  
	manning_sea
	  :description:		Varying manning roughness based on elevation (below 'rgh_level_land', overules uniform 'manning', specify in s/m^(1/3).
	  :units:		s/m^(1/3)
	  :default:		-999 (=not used)
	  :min:			0
	  :max:			Inf  	  
	  
Parameters for model input (only for advanced users)
-----
	bndtype        
	  :description:		Boundary type for interpretation of 'sfincs.bzs' time-series. bndtype=1 is for water levels, bndtype=2 is for horizontal velocities (in m/s) and bndtype=3 for horizontal discharges (in m2/s).
	  :units:		-
	  :default:		1
	  :min:			1
	  :max:			3
	rhoa
	  :description:		Density of the air
	  :units:		-
	  :default:		1.25
	  :min:			-
	  :max:			-
	rhow
	  :description:		Density of the water
	  :units:		-
	  :default:		1024
	  :min:			-
	  :max:			-
	stopdepth
	  :description:		Water depth anywhere in the domain after which the simulation is classified as unstable and stopped
	  :units:		m
	  :default:		100
	  :min:			0
	  :max:			Inf	  
	advlim
	  :description:		Advection limiter when advection>0 to limit the magnitude of the advection term when calculating fluxes between cells.
	  :units:		-
	  :default:		9999
	  :min:			0
	  :max:			9999
	dtmax
	  :description:		Maximum internal time step to be used
	  :units:		s
	  :default:		60
	  :min:			1.0e-3
	  :max:			Inf
	dtmin
	  :description:		Minimum internal time step to be used
	  :units:		s
	  :default:		1.0e-3
	  :min:			1.0e-3
	  :max:			Inf	  
	tspinup
	  :description:		Duration of internal spinup period before tstart
	  :units:		s
	  :default:		0
	  :min:			0
	  :max:			Inf
	  
	**Drag coefficients:**
	
	cdnrb
	  :description:		Number of specified break points
	  :units:		-
	  :default:		3
	  :min:			2
	  :max:			-	
	cdwnd	  
	  :description:		Wind speed break points (including 0)
	  :units:		-
	  :default:		0  28  50
	  :min:			2 values
	  :max:			-
	  :description:		Drag coefficient brak points
	  :units:		-
	  :default:		0.001 0.0025 0.0015
	  :min:			2 values
	  :max:			-	  
	
Different parameters influencing the given output by SFINCS can be changed, see below. 

Parameters for model output
-----

	tref
	  :description:	Reference date in 'yyyymmdd HHMMSS'
	  :units:	-
	  :default:	20000101 000000
	tstart
	  :description:	Start date in 'yyyymmdd HHMMSS'
	  :units:	-	
	  :default:	20000101 000000				  
	tstop
	  :description:	Stop date in 'yyyymmdd HHMMSS'
	  :units:	m
	  :default:	20000101 000000
	dtout
	  :description:	Time-step global map output.
	  :units:	s
	  :default:	0
	dthisout
	  :description:	Time-step observation points output.
	  :units:	s
	  :default:	600
	dtmaxout
	  :description:	Time-step interval of global map output of maximum water level. If dtmaxout=0, no maximum water level output is given by SFINCS
	  :units:	s
	  :default:	0
	  :min:		0
	  :max:		'tstop - start in seconds'  	  
	dtwnd
	  :description:	Time-interval wind update (only for spiderweb)
	  :units:	s
	  :default:	1800
	outputformat
	  :description:	Choice whether the SFINCS model output is given in binary 'bin', ascii 'asc' or netcdf files 'net'(default). In case of netcdf output, global output is given in 'sfincs_map.nc', point output in 'sfincs_his.nc' in case observation points are specified.
	  :units:	-
	  :default:	net
		
