# Burning fuel for cheap! Transport-independent depletion in OpenMC

## Abstract
OpenMC is an open-source, community-developed software for neutron transport
simulations, featuring a depletion module for fuel burnup calculations in
nuclear reactors. Depletion calculations can be expensive as they require an
iterative solution to the neutron transport equation and material composition
updates .In a scenario where the material composition does not appreciably
change, or we need reasonably accurate and low cost depletion, the transport
solution may only need to be run once; the same cross sections are used for the
entire depletion calculation.  We recently extended the depletion module in
OpenMC to enable transport-independent depletion using multigroup cross sections
and fluxes. This talk will focus on the technical details of this feature, its
validation, and areas where the feature has been used, in particular in
calculating shutdown dose rates for fusion power applications as well as in
performing depletion for fuel cycle modeling.

## Description
Neutron radiation of the fuel inside of a nuclear reactor induces nuclear
fission in certain nuclides like U235. The fission reaction causes the nucleus
to break apart, releasing both energy and new nuclides, many of which are
radioactive isotopes of smaller elements. This process is referred to as
depletion or burnup. We model this process to design and license new reactors as
depletion can effect performance and determines when the fuel must be shuffled
or replaced. The typical approach to modeling depletion requires solving the
neutron transport equation to obtain reaction rates which govern the material
composition at the next time step. This process is repeated iteratively
(transport-coupled depletion).

OpenMC is an open-source neutron transport code with a built-in depletion
module. OpenMC solves the transport equation via Monte Carlo particle transport,
which is accurate but expensive. OpenMC's depletion module was recently extended
to enable depletion modeling without iteratively solving the transport equation
(transport-independent depletion). Instead, the transport equation is solved
once, and multigroup cross sections and fluxes are obtained from this solution.
The multigroup cross sections and fluxes are used for every timestep of the
depletion calculation. This method is accurate for the first timestep, but
degrades at further timesteps. Testing with a simple model indicated errors
depend on the nuclide of interest. 

In this talk, I will cover:
- The physics and mathematics of depletion
- Accuracy of transport-independent depletion compared to transport-coupled
    depletion.
- Two applications where transport-independent depletion has been used to great
    effect: shutdown dose-rate calculations for fusion energy applications, and
    fast depletion for fuel cycle analysis.

The intended audience of this talk are folks who are interested in nuclear
engineering and open-source software.

## Notes
This could also be in the "Celebrating the 'Sci' in SciPy" track.
