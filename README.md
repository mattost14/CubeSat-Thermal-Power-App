# CubeSat Thermal Power Toolbox

This MATLAB App is intended to provide a quick and easy way to perform preliminary thermal and power analysis for CubeSat missions. This is particularly usefull during the first phases of the project life-cycle. 

# How to use it
## Step 1) Generate the Orbit

Propagate the orbit and enter the central body thermal parameters for Solar FLux, Albedo and IR.

The tool currently provides options for Earth or Moon orbits.

### Earth orbits
Propagator options: two-body-keplerian and SGP4.
### Moon orbits
Propagator options: Kepler and Numerical (high precision). 
The Numerical propagator uses the spherical harmonics (LP-100K) as gravity model.
#### Moon IR model
For the Moon IR model, the user can select the "Gradient" option. In this case, the surface temperature is modeled by the analytical expression provided in the [Human Landing System Lunar Thermal Analysis Guidebook](https://ntrs.nasa.gov/api/citations/20210010030/downloads/HLS-UG-001%20Lunar%20Thermal%20Analysis%20Guidebook%20Baseline_STI.pdf), Section 4.3, Pag 17. The IR flux is later computed by integrating the Moon's sphere discretized with 1 degree step. 

## Step 1) Model your CubeSat

CubeSat size options: 1U, 3U, 6U, 12U

For each face, select the cover material. Each built-in material offers different thermal-optical properties. The user can also enter a custom material with different values for absorptivity, emissivity and specific heat. If face is body-fixed solar panel, the user must enter the cell efficiency and packing factor.

#### Deployable
The user can also define the deployable solar panels, either Fixed or Sun-Tracking. The deployable panels are only used to computed the generated power and they are not considered in the thermal analysis.

### Lumped thermal model
The current version uses a 7-Nodes lumped thermal modeled using Simscape. The schematic is presented in the Figure below.

# Instalation
To install, simply run the 'CubeSat Thermal Power Toolbox.mlappinstall' file. After instalation, the app will be available on the Apps tab inside MATLAB.

On this MATLAB app (GUI) you can:
1) Propagate Earth/Moon orbit;
2) Model your CubeSat by selecting its size, surface materials and properties, deployable solar panels, and internal thermal resistances;
3) Compute the generated solar power, power consumption, and power budget;
4) Compute the thermal loads and nodes temperatures using a simple lumped thermal capacity model;

[![View CubeSat Thermal Power App on File Exchange](https://www.mathworks.com/matlabcentral/images/matlab-file-exchange.svg)](https://www.mathworks.com/matlabcentral/fileexchange/126240-cubesat-thermal-power-app)
