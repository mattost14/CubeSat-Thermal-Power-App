# CubeSat Thermal Power Toolbox

This MATLAB App is intended to provide a quick and easy way to perform preliminary thermal and power analysis for CubeSat missions. This is particularly usefull during the first phases of the project life-cycle.


https://www.youtube.com/watch?v=L0wHe530bRc&t=195s


# Instalation
To install, simply run the 'CubeSat Thermal Power Toolbox.mlappinstall' file. After instalation, the app will be available on the Apps tab inside MATLAB.

# How to use it
## Step 1) Generate the Orbit

Propagate the orbit and enter the central body thermal parameters for Solar FLux, Albedo and IR.

The tool currently provides options for Earth or Moon orbits.

#### Earth orbits
Propagator options: two-body-keplerian and SGP4.
#### Moon orbits
Propagator options: Kepler and Numerical (high precision). 
The Numerical propagator uses the spherical harmonics (LP-100K) as gravity model.
#### Moon IR model
For the Moon IR model, the user can select the "Gradient" option. In this case, the surface temperature, see Figure below, is modeled by the analytical expression provided in the [Human Landing System Lunar Thermal Analysis Guidebook](https://ntrs.nasa.gov/api/citations/20210010030/downloads/HLS-UG-001%20Lunar%20Thermal%20Analysis%20Guidebook%20Baseline_STI.pdf), Section 4.3, Pag 17. The IR flux is later computed by integrating the Moon's sphere discretized with 1 degree step. 

<p align="center">
  <img src="https://github.com/mattost14/CubeSat-Thermal-Power-App/blob/main/Figures/MoonSurfaceTemp.png" height="300">
</p>

## Step 2) Model your CubeSat

CubeSat size options: 1U, 3U, 6U, 8U, 12U

For each face, select the cover material. Each built-in material offers different thermal-optical properties. The user can also enter a custom material with different values for absorptivity, emissivity and specific heat. If face is body-fixed solar panel, the user must enter the cell efficiency and packing factor.

#### Deployable
The user can also define the deployable solar panels, either Fixed or Sun-Tracking. The deployable panels are only used to computed the generated power and they are not considered in the thermal analysis.

#### Lumped Parameter Model 
The current version runs the thermal analysis of the CubeSat with a 7-Nodes Lumped Parameter Model using Simscape. The schematic is presented in the Figure below.

<p align="center">
  <img src="https://github.com/mattost14/CubeSat-Thermal-Power-App/blob/main/Figures/ThermalModel7NodesSchematic.png" height="300">
</p>

The user shall input the best estimate for each thermal resistance linking the internal node (Node 1) to each face node.

The thermal mass of each node is specified by the mass distribution and specific heat inputs.

This thermal model does NOT considered:

* Heat transfer between faces;
* Internal heat transfer by radiation;
* Heat transfer with external surfaces (deployables)

## Step 3) Compute Power

The user enters the internal node dissipation power by either defining it as a constant value or by defining two power dissipation levels depending on whether the satellite is illuminated by the Sun or in an eclipse.

The tool offers total power generation and battery charge depletion throughout the orbit.

When the satellite is charging the battery, the satellite faces with body-fixed solar panels have their absoportion coefficients reduced to account for the power conversion. 

## Step 4) Run Thermal Analysis

The tool offers the total accumulated radiation input coming from the Sun, central body IR, and Albedo reflection.

Finally, the internal node temperature and the faces nodes temperatures are plotted.


[![View CubeSat Thermal Power App on File Exchange](https://www.mathworks.com/matlabcentral/images/matlab-file-exchange.svg)](https://www.mathworks.com/matlabcentral/fileexchange/126240-cubesat-thermal-power-app)

