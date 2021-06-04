Output description
======================

In case of netcdf output, the given parameters mean the following:

Parameters netcdf file global (sfincs_map.nc):
----------------------

	x
	  :description:	Reference date in 'yyyymmdd HHMMSS'
	  :units:	m in projected reference system
	y
	  :description:	Start date in 'yyyymmdd HHMMSS'
	  :units:	m in projected reference system
	zb
	  :description:	Stop date in 'yyyymmdd HHMMSS'
	  :units:	m
	msk
	  :description:	Time-step global map output.
	  :units:	-
	zs
	  :description:	Instantaneous water level per 'dtout' timestep, corresponding with netcdf variable 'time' 
	  :units:	m above reference level
	h
	  :description:	Time-interval wind update (only for spiderweb)
	  :units:	m
	zsmax
	  :description:	Maximum water level per 'dtmaxout' timestep, only given if dtmaxout>0, corresponding with netcdf variable 'timemaxout' 
	  :units:	m above reference level
	inp
	  :description:	Copy of all the supplied input to SFINCS from 'sfincs.inp'.
	  :units:	-
	  
Parameters netcdf file observation points (sfincs_his.nc):
----------------------		
