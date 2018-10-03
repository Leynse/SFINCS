Input parameters
=====

Different input parameters can be changed, see below. Traditionally SFINCS neglects the advection term in the SFINCS-LIE version ('advection = 0'). 
For super-critical flow conditions or modelling waves, the SFINCS-SSWE version can be used ('advection = 1' for 1D modelling and 'advection = 2' for 2D modelling) for better performance. 


Parameters
-----


	advection
	  :description:		setting for advection. 0 for no advection scheme (SFINCS-LIE), 1 for 1D advection scheme for modelling in 1D OR 2 for 2D advection scheme for modelling in 2D (SFINCS-SSWE).
	  :units:		-
	  :default:		0
	  :min:			0
	  :max:			2
	alpha	
	  :description:		CFl-condition reduction. Decrease for additional numerical stability, minimum value is 0.1 and maximum is 0.75.
	  :units:		-	
	  :default:		0.75		
	  :min:			0.1	
	  :max:			0.75		  
	huthresh	
	  :description:		Minimum flow depth limiter.
	  :units:		m
	  :default:		0.05
	  :min:			0
	  :max:			-
	theta
	  :description:		Smoothing factor in momentum equation. Advised not too change.
	  :units:		-
	  :default:		0.9
	  :min:			0
	  :max:			1
	zsini
	  :description:		Initial water level.
	  :units:		m
	  :default:		0
	  :min:			-
	  :max:			-
	qinf
	  :description:		Infiltration rate. specify in -m^3/s (negative sign for infiltration)!
	  :units:		m^3s^-1
	  :default:		0
	  :min:			-
	  :max:			0  
		
