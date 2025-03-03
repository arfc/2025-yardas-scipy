# Burning fuel for cheap! Transport-independent depletion in OpenMC

## Abstract
OpenMC is an open source, community-developed, Monte Carlo tool for neutron
transport simulations, featuring a depletion module for fuel burnup calculations
in nuclear reactors and a Python API. Depletion calculations can be expensive as they require
solving the neutron transport and bateman equations in each timestep to update
the neutron flux and material composition, respectively. Material properties
such as temperature and density govern material cross sections, which in turn
govern reaction rates. The reaction rates can effect the neutron population. In
a scenario where there is no significant change in the material properties or
composition, the transport simulation may only need to be run once; the same
cross sections are used for the entire depletion calculation. We recently
extended the depletion module in OpenMC to enable transport-independent
depletion using multigroup cross sections and fluxes. This talk will focus on
the technical details of this feature, its validation, and briefly touch on
areas where the feature has been used. Two recent use cases will be highlighted.
The first use case calculates shutdown dose rates for fusion power 
applications, and the second performs depletion for fission reactor fuel cycle modeling.

## Description
Neutrons can induce nuclear fission in fissile nuclides like <sup>235</sup>U. The fission
reaction causes the nucleus to break apart, releasing both energy and new
nuclides, many of which are radioactive isotopes of smaller elements. In nuclear
reactors, which are fueled by fissionable material, this process is referred to
as depletion, or burnup. Nuclear engineers model this process to design and license new
reactors.  Depletion can affect reactor physics and performance, and determines
when the fuel must be shuffled or replaced. The typical approach to modeling
depletion requires solving the neutron transport equation to obtain the neutron
flux, which changes reaction rates in the fuel. These reaction rates inform the
material composition at the next time step. This process is repeated each time
step and is called transport-coupled depletion.

OpenMC is an open source neutron transport code with a built-in depletion
module. OpenMC solves the transport equation via Monte Carlo particle transport,
which is accurate but expensive. OpenMC's depletion module was recently extended
to enable depletion modeling without solving the transport equation at each time
step. Instead, the transport equation is solved once. From this solution, the
flux of neutrons and their cross sections are discretized in energy and
normalized. These are called multigroup fluxes and cross sections, 
respectively, and are used during every time step of the
depletion calculation. The process is called transport-independent depletion.
This method is accurate for the first time step, but degrades at further time
steps. Testing with a simple model indicates that the error with respect to
transport-coupled depletion depends on the nuclide of interest. 

In this talk, I will cover:
- A brief background on the physics and mathematics of depletion,
- the accuracy of transport-independent depletion compared to
  transport-coupled depletion,
- and two applications where
  transport-independent depletion has been used to great effect: shutdown
  dose-rate calculations for fusion energy applications, and fast depletion for
  fuel cycle analysis.

The intended audience of this talk are people interested in nuclear reactor
systems and open source software.

## Notes
This could also be in the General track.
Contributors to this work include Dr. Paul Romano, Prof. Madicken Munk, and 
Prof. Kathryn Huff.
[Transport independent depletion documentation](https://docs.openmc.org/en/stable/usersguide/depletion.html#transport-independent-depletion)
[Shutdown Dose Rate paper](https://dx.doi.org/10.1088/1741-4326/ad32dd)
[Fuel cycle paper](https://doi.org/10.1080/00295639.2024.2393940)
