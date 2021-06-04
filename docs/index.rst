.. SFINCS documentation master file, created by
   sphinx-quickstart on Tue Jun 13 09:56:18 2017.
   You can adapt this file completely to your liking, but it should at least
   contain the root `toctree` directive.

Welcome to SFINCS's documentation!
======================================

'SFINCS' is the reduced-complexity model designed for super-fast modelling of compound flooding events in a dynamic way!

.. figure:: ./figures/Figure_coastal_model.png
   :width: 600px
   :align: center
   
* For an introduction of the model see the journal publication: https://doi.org/10.1016/j.coastaleng.2020.103796

* For a second application in tsunami modelling see the journal publication: https://doi.org/10.3390/jmse9050453

* More information regarding recent advancements with subgrid features can be seen in this online poster: https://agu2020fallmeeting-agu.ipostersessions.com/Default.aspx?s=9C-05-18-CF-F1-2B-17-F0-7A-21-93-E6-13-AE-F3-24

This online documentation describes the input files and parameters of the SFINCS model (Super-Fast INundation of CoastS).
The documentation is however still under construction, mail 'tim.leijnse@deltares.nl' for questions that are not answered yet by this documentation.
Also let us know when you are not yet a user of SFINCS, but are interested to get started!
The SFINCS executable is not yet shared open source, but will be in the future, and maybe in the meantime a collaboration is possible.

Documentation
=============

**Introduction**

* :doc:`overview`

.. toctree::
   :maxdepth: 2
   :hidden:   
   :caption: Introduction:
   
   overview
   
**User manual**  

* :doc:`input`
* :doc:`input_forcing`
* :doc:`input_structures`

.. toctree::
   :maxdepth: 3
   :hidden:
   :caption: User manual:
   
   input
   input_forcing
   input_structures
   
**Overview input parameters and files**   

* :doc:`parameters`

.. toctree::
   :maxdepth: 3   
   :hidden:
   :caption: Input parameters and files:
   
   parameters
   
**Overview model output and messages**   

* :doc:`output`

.. toctree::
   :maxdepth: 3   
   :hidden:
   :caption: Model output and messages:
   
   output
   
**Getting started**    

* :doc:`example`

.. toctree::
   :maxdepth: 3   
   :hidden:
   :caption: Getting started:
   
   example
   
    
Acknowledgements
================

SFINCS is developed at Deltares and initiated by Maarten van Ormondt.
This documentation is developed and maintained by Tim Leijnse and Roel de Goede.



