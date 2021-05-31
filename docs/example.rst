Setting up models
=======

Introduction 
----------------------

SFINCS models can be setup using simple ascii text and binary input files, which can be generated on whatever platform suiting you as a user best.
To make the setting up of basic models easier, making a SFINCS model is supported by the two easy setup tools called 'Delft Dashboard' and 'HydroMT'.
These options do not cover setting up subgrid feature type models yet, which is still an advanced user functionality.
Additionaly, a range of Matlab scripts exist for setting up SFINCS models using the Open Earth Tools for more user flexibility.
If you need a more tailor-made solution for setting up your SFINCS models get in touch with us!

Delft Dashboard 
----------------------

Delft dashboard (Van Ormondt et al. 2020 https://doi.org/10.2166/hydro.2020.092) is a quick set-up tool for hydrodynamic models that includes setting up SFINCS models.
The tool can be run on Matlab or as standalone executable and has all the basic functionality to setup your basic model using globally available DEMs.
For more information see: https://publicwiki.deltares.nl/display/DDB

HydroMT 
----------------------

HydroMT is a more recent addition to the tools available for setting up SFINCS models, and is a Python based alternative.
Besides globally available DEMs it can also retrieve spatially varying infiltration and manning roughness data based on landuse maps.
Also, it is possible to setup a offline coupled model together with the hydrological wflow model that will provide boundary conditions of river discharge.
For more information regarding the SFINCS plugin of HydroMT see: https://deltares.github.io/hydromt_sfincs/
For more information regarding HydroMT in general see: https://deltares.github.io/hydromt/

Open Earth Tools
----------------------

In the Open Earth Tools section of DDB, a number of Matlab scripts are included to have more flexibility in setting up your SFINCS models.
Throughout the User Manual examples of how to use these scripts are given in the code blocks '**Matlab example using OET**'.
For a general overview of possible input files and how to create them using Matlab scripts see: https://svn.oss.deltares.nl/repos/openearthtools/trunk/matlab/applications/DelftDashBoard/general/sfincs/fileio/Input_format_examples.m
For getting started with Open Earth Tools see: https://publicwiki.deltares.nl/display/OET/OpenEarth

