Input parameters
=====

Different input parameters can be changed, see below. Traditionally SFINCS neglects the advection term in the SFINCS-LIE version ('advection = 0'). 
For super-critical flow conditions or modelling waves, the SFINCS-SSWE version can be used ('advection = 1' for 1D modelling and 'advection = 2' for 2D modelling) for better performance.        
     
Parameters
-----

.. partable:: Overview of available keywords related to *

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
	  :min:			0.001
	  :max:			0.2
	theta
	  :description:		Smoothing factor in momentum equation. Advised not too change.
	  :units:		-
	  :default:		0.9
	  :min:			0.8
	  :max:			0.99
	zsini
	  :description:		Initial water level.
	  :units:		m
	  :default:		0
	  :min:			-Inf
	  :max:			Inf
	qinf
	  :description:		Infiltration rate. specify in +mm/hr
	  :units:		m/s
	  :default:		0
	  :min:			0
	  :max:			Inf  
		
