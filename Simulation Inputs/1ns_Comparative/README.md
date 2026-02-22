# 1-ns Comparative Molecular Dynamics Simulations

This directory contains input files used for the short (1-ns) comparative all-atom molecular dynamics simulations described in Section 2.6.3 of the manuscript.

## Systems Simulated

Simulations were performed under identical conditions for:

- DUSP15 (AlphaFold structural model)
- DUSP7 (AlphaFold structural model; catalytically competent MAPK phosphatase)

## Simulation Software

- GROMACS 2024.2 (single precision)
- AMBER99SB-ILDN force field
- TIP3P explicit water model

## System Preparation

- Cubic simulation box with ≥1.0 nm padding
- Explicit solvation
- Neutralization with counterions:
  - DUSP15: 7 Cl⁻
  - DUSP7: 16 Na⁺

## Energy Minimization

- Steepest descent algorithm
- Maximum 50,000 steps
- Convergence criterion: Fmax < 500 kJ·mol⁻¹·nm⁻¹

## Equilibration

- 100 ps NVT at 300 K (V-rescale thermostat)
- 200 ps NPT at 300 K and 1 bar (Parrinello–Rahman barostat)
- LINCS constraints applied to hydrogen-containing bonds
- PME used for long-range electrostatics

## Production Dynamics

- 1 ns unrestrained NPT simulation
- 2 fs integration timestep
- Coordinates saved every 2 ps

These short simulations were designed specifically for controlled dynamical comparison between DUSP15 and DUSP7 under identical atomistic conditions rather than for extended equilibrium sampling.
