Overview
=======

Introduction to SFINCS
----------------------

SFINCS is a reduced-complexity model for modelling compound flooding in an accurate but computationally efficient way. 
Generally speaking, compound flooding is described as extreme events occurring in coastal areas where the interaction of joint high sea level and a large amount of precipitation causes extreme flooding. 
However, in coastal areas, wave-driven flooding can also have a large contribution to occurring flooding events. 

For probabilistic risk assessments and early warning systems, rapid inundation models are needed. 
SFINCS is aimed to be computationally efficient while remaining sufficiently accurate. 
The current version of SFINCS is able to solve traditional types of compound flooding regarding high offshore water levels, precipitation, wind-induced setup and wave-driven processes. 

In SFINCS a set of momentum and continuity equations are solved with a first order explicit scheme based on Bates et al. (2010).
Traditionally SFINCS neglects the advection term (SFINCS-LIE) which generally justified for sub-critical flow conditions. 
For super-critical flow conditions or when modelling waves, the advection term needs to be solved. 
For this purpose, the SFINCS-SSWE version can be used (including advection).
For more information see Leijnse et al. (2020): https://doi.org/10.1016/j.coastaleng.2020.103796

Types of environments for SFINCS models
-----
>TODO: add figures of coastal, riverine, urban, tsunami and compound flooding type SFINCS models<

Coastal model
^^^^^^^^^

A SFINCS model in coastal regions can be forced with marine forcings like tides, storm surge, local wind setup and wave driven processes.
Generally a model is setup with the offshore boundary in the swash zone, good practice is in about 2 meters water depth.
In SFINCS it is possible to distinguish cells that are made inactive in the computation so it will not slow your model down (in this case everywhere deeper than 2m water depth).
In some cases local rainfall might be relevant too for a coastal model.

Coral reef model
^^^^^^^^^
SFINCS models have also been setup in coral reef type environments, where individual waves are forced to compute wave-driven flooding.
This generally has a large contribution to flooding for Small Island Developping States (SIDS) or other coasts/islands with coral reef type coasts.

Riverine model
^^^^^^^^^
For inland riverine types of environments, boundary conditions are generally different than for coastal models.
Generally at the upstream end of rivers, one can provide discharge points with discharge time-series.
At the downstream end of rivers, water level time-series need to be specified, which in case of sub-critical flow conditions will influence the flow upstream.
Additionaly, besides the general river discharge, local rainfall adding water to the river can be very relevant too.

Urban model
^^^^^^^^^
For urban environments the local situation of varying land use conditions can heavily influence the local flow.
Therefore spatially varying input of manning roughness and infiltration is possible.
The curve number method of infiltration will distinguish what part of falling precipitation can infiltrate or will run-off.
To test out the effect of interventions, it is possible to insert different types of structures into the SFINCS model.
These can be thin dams, levees, sea walls, simple drainage pumps or culverts.

(Flash flood model)
^^^^^^^^^

(Tsunami model)
^^^^^^^^^

(Storm surge model)
^^^^^^^^^

Compound flooding model
^^^^^^^^^
In a compound flooding model, all relevant types of forcing from either coastal, coral, riverine or urban models can be combined into 1 domain.
Hereby the joint effect of multiple flood drivers that can enhance flooding can be taken into account.

Overview domain
-----

To setup a SFINCS model, a few different layers are relevant to describe the wanted domain.

Elevation
^^^^^^^^^
To describe the local topography and bathymetry, elevation data has be supplied to the model.
This can be of any multiple of sources, but it is advised that the transition zone between different datasets and between above/below water level are checked with care.
The elevation is described in the cell centres of the grid.

Subgrid tables
^^^^^^^^^
Currently the SFINCS model functionality is extended so that SFINCS can also calculated flooding with the use of subgrid tables.
Hereby high-resolution elevation data is used to derive relations between the water level and the volume in a cell to do the continuity update, and a representative water depth used to calculate momentum fluxes.
The derivation of these subgrid tables is a pre-processing step outside of the model, that only needs to be done once!
The advantage of the subgrid version of SFINCS is that generally one can compute on coarsed grid sizes, while still having accurate results utilizing the high-resolution elevation data to its full potential.
TODO: add figure of Maarten

Mask
^^^^^^^^^
To distinguish active from inactive areas and cells where boundary conditions need to be forced, a mask file needs to be supplied.
This mask indicates for every cell whether it is an inactive cell (msk=0), active cell (msk=1) or boundary cell (msk=2).
This allows great flexibility in optimising the model domain and thereby reducing the computational runtime as much as possible.

Manning roughness
^^^^^^^^^
Different roughness values can great impact modelled flooding and thereby SFINCS allows the specification of a uniform value, differentiating land and sea with 2 different values or specifying a specific value per grid cell.

Infiltration
^^^^^^^^^
Infiltration can significantly alter the amount of flooding when including precipitation.
SFINCS allows the specification of a uniform constant value, spatially varying constant value or the Curve Number method.
The Curve Number is a generally used method to determine what parts of falling rainfall can infiltrate or will run-off, hereby a limited time component is taken into account as well.

Initial water level
^^^^^^^^^
The water level is by default initiated at 0 meters above mean water level, but can be changed.
In the initialisation phase within the model, all cells with an elevation below specified user value are given the specified value, thereby starting without a completely dry bed.
For more flexibility, this can also be prescribed spatially varying which can be relevant for coastal, riverine and tsunami cases.

Observation points
^^^^^^^^^
For more detailed information besides map output, observation points can be added for higher temporal resolution output information.

Overview types of forcing
-----

SFINCS has different functionalities regarding different relevant physical processes for compound flooding and what type of model is required. 
At first nearshore/offshore water levels can be specified at the different locations along the coast to include tides and storm surge levels. 
Inland drivers of flooding like precipitation and wind can be specified in a number of ways.  
This varies from simple spatially uniform time-series to spatially varying spiderwebs or grid input types.  
Furthermore, simple implementations for discharges and infiltration are included, as well as a spatially varying roughness fields.

MENTION SOMETHING ABOUT TROPICAL CYCLONES

Water levels
Waves
Discharge
Wind
Rainfall

Overview types of structures
-----