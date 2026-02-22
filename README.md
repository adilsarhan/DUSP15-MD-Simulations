# DUSP15 Molecular Dynamics Simulations

This repository contains molecular dynamics (MD) input files and processed time-series datasets supporting the manuscript:

**Sarhan AR.**  
*DUSP15 Exhibits Structural and Dynamical Signatures Inconsistent with Catalytic Phosphatase Activity.*  
BBA – Proteins and Proteomics.

---

## Repository Structure

### Simulation Inputs
Contains all structural and parameter files required to reproduce the simulations.

- `100ns_DUSP15/`
  - 100-ns all-atom MD simulation of the crystallographically resolved catalytic domain of DUSP15 (PDB ID: 1YZ4).
  
- `1ns_Comparative/`
  - Short (1-ns) controlled comparative simulations of:
    - DUSP15 (AlphaFold model)
    - DUSP7 (AlphaFold model)

---

### Processed Time-Series Data
Contains processed CSV files used to generate Figures 5 and 6.

- `100ns_DUSP15/`
  - Global RMSD
  - Motif RMSD (residues 75–95)
  - RMSF
  - Radius of gyration
  - Motif SASA
  - Intramolecular contacts
  - Minimum distances
  - Hydration metrics

- `1ns_Comparative/`
  - Equivalent metrics for DUSP15 and DUSP7 under identical simulation conditions.

For the comparative simulations, statistical summaries reported in the manuscript were calculated over the final 200 ps (800–1000 ps) of each 1-ns trajectory to minimize potential equilibration effects.

---

## Software and Force Field

All simulations were performed using:

- GROMACS 2024.2
- AMBER99SB-ILDN force field
- TIP3P explicit water model
- PME electrostatics
- 2 fs integration timestep

Full simulation protocols are described in Sections 2.6.2 and 2.6.3 of the manuscript.

---

## Reproducibility

This repository contains:

- Structural input files (.pdb)
- GROMACS parameter files (.mdp)
- Topology files (.top)
- Processed time-series data (.csv)

Raw trajectory files are not included due to size constraints but can be regenerated using the provided inputs and parameters.

---

## Contact

For questions regarding the simulations or data structure, please contact:

Dr. Adil R. Sarhan
