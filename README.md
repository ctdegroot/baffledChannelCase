# Domain

The domain is shown in the image below:

![Domain](https://raw.githubusercontent.com/ctdegroot/baffledChannelCase/master/Images/Domain.png?raw=true)

The blue surface is the inlet of the domain and the green surface is the outlet. All of the magenta surfaces are walls. There is also a wall at the top of the domain, which is not shown.

The mesh is created using `blockMesh`. Baffles are created by finding common faces between adjacent blocks using `topoSet` and creating the baffles using `createBaffles`.

# Boundary Conditions

| Boundary Name | Velocity BC | Pressure BC | k BC | epsilon BC |
|---------------|-------------|-------------|------|------------|
| inlet         | flowRateInletVelocity | fixedFluxPressure | turbulentIntensityKineticEnergyInlet | turbulentMixingLengthDissipationRateInlet |
| oulet         | zeroGradient | fixedValue | zeroGradient | zeroGradient |
| top           | slip | fixedFluxPressure | kLowReWallFunction | epsilonWallFunction |
| bottom        | noSlip | fixedFluxPressure | kLowReWallFunction | epsilonWallFunction |
| walls         | noSlip | fixedFluxPressure | kLowReWallFunction | epsilonWallFunction |
| baffle.\*     | noSlip | fixedFluxPressure | kLowReWallFunction | epsilonWallFunction |


# Solver

This case is solved using the steady state solver `simpleFoam`.
