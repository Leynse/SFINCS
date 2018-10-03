Overview
=======

Introduction to SFINCS
----------------------

SFINCS is a semi-advanced model for modelling compound flooding in an accurate but computationally efficient way. Generally speaking, compound flooding is described as extreme events occurring in coastal areas where the interaction of joint high sea level and a large amount of precipitation causes extreme flooding. 
However, in coastal areas, wave-driven flooding can also have a large contribution to occurring flooding events. 

For probabilistic risk assessments and early warning systems, rapid inundation models are needed. SFINCS is aimed to be computationally efficient while remaining sufficiently accurate. The modelling approach with SFINCS is to simulate the water levels from the swash zone to the region inland. The current version of SFINCS is able to solve traditional types of compound flooding regarding high offshore water levels, precipitation and wind-induced setup. For the future version of SFINCS also wave-driven processes will be included so that wave-driven flooding (e.g. overtopping) can be included as well. Traditionally SFINCS neglects the advection term (SFINCS-LIE) which generally justified for sub-critical flow conditions.  For super-critical flow conditions or when modelling waves, the advection term needs to be solved. For this purpose, the SFINCS-SSWE version can be used.


Overview functionalities
-----

SFINCS has different functionalities regarding different relevant physical processes for compound flooding. At first nearshore/offshore water levels can be specified at the different locations along the coast to include tides and storm surge levels. Inland drivers of flooding like precipitation and wind can be specified in a number of ways.  This varies from simple spatially uniform time-series to spatially varying spiderwebs or grid input types.  Furthermore, simple implementations for discharges and infiltration are included, as well as a spatially varying roughness fields.


