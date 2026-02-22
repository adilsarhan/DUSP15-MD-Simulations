DUSP15 – 100-ns All-Atom Molecular Dynamics Simulation

This repository contains molecular dynamics (MD) input files and processed trajectory analyses supporting the manuscript:

Sarhan AR.
DUSP15 Exhibits Structural and Dynamical Signatures Inconsistent with Catalytic Phosphatase Activity.
BBA – Proteins and Proteomics.

---

Overview

This repository provides the necessary input files and processed outputs to reproduce the 100-ns all-atom MD simulation of the catalytic domain of human DUSP15 and the trajectory analyses reported in Figure 5 of the manuscript.

The simulation was designed to evaluate:
	•	Global structural stability
	•	Catalytic motif rigidity (residues 75–95)
	•	Intramolecular packing density
	•	Solvent accessibility
	•	Hydration properties of the active-site region

All analyses are derived from the 100-ns production trajectory described in the manuscript under standard atomistic simulation conditions.

---

Structural Model
	•	Starting structure: X-ray crystal structure of the catalytic domain of human DUSP15
	•	PDB ID: 1YZ4
	•	Chain A retained
	•	Simulation restricted to the crystallographically resolved catalytic domain

The deposited crystal structure contains an engineered substitution at the putative catalytic position in which the native cysteine is modeled as serine (Ser88).
To restore the native catalytic identity while preserving backbone geometry and local structural context, a Ser→Cys substitution (S88C) was introduced using PyMOL mutagenesis prior to system preparation. No backbone rearrangements were introduced.

---

Simulation Software
	•	MD engine: GROMACS 2024.2
	•	Force field: AMBER99SB-ILDN
	•	Water model: TIP3P
	•	Long-range electrostatics: Particle Mesh Ewald (PME)
	•	Cutoff scheme: Verlet
	•	Periodic boundary conditions applied in all dimensions

---

System Preparation
	•	Simulation box: Cubic
	•	Minimum solute–box edge distance: 1.0 nm
	•	Explicit solvent: TIP3P water
	•	Counter-ions: Cl⁻ added to neutralize the system

---

Energy Minimization
	•	Algorithm: Steepest descent
	•	Convergence criterion: Maximum force < 1000 kJ·mol⁻¹·nm⁻¹

---

Equilibration Protocol

Two-stage equilibration was performed with positional restraints applied to protein heavy atoms.

NVT (500 ps)
	•	Temperature: 300 K
	•	Thermostat: V-rescale
	•	Separate coupling groups for protein and non-protein atoms

NPT (500 ps)
	•	Temperature: 300 K
	•	Pressure: 1 bar
	•	Barostat: Parrinello–Rahman
	•	Isotropic pressure coupling

---

Production Molecular Dynamics
	•	Duration: 100 ns
	•	Ensemble: NPT
	•	Temperature: 300 K
	•	Pressure: 1 bar
	•	Time step: 2 fs
	•	Hydrogen bond constraints: LINCS
	•	Electrostatic real-space cutoff: 1.0 nm
	•	van der Waals cutoff: 1.0 nm
	•	Trajectory coordinates and energies saved every 10 ps

All quantitative analyses reported in the manuscript are derived from this 100-ns production trajectory.

---

Analyses Performed

The following analyses were computed using standard GROMACS utilities:
	•	Global backbone RMSD
	•	Motif-specific backbone RMSD (residues 75–95)
	•	Per-residue Cα RMSF
	•	Radius of gyration (Rg)
	•	Solvent-accessible surface area (SASA) of motif backbone
	•	Intramolecular contact counts between the motif and the remainder of the protein (0.45 nm cutoff)
	•	Minimum interatomic distances between motif and non-motif regions
	•	Hydration analysis: number of water oxygen atoms within 0.35 nm of defined atom groups
Statistical descriptors were computed across the full 100-ns trajectory.

---

Repository Structure

Simulation Inputs/
The following files are required to reproduce the 100-ns MD simulation:
	•	1yz4.pdb: Starting structure (S88C restored)
	•	topol.top: System topology
	•	em.mdp: Energy minimization parameters
	•	nvt.mdp: NVT equilibration parameters
	•	npt.mdp: NPT equilibration parameters
	•	md_100ns.mdp: Production MD parameters

Processed Time-Series Data/
The following extracted datasets (.csv) were used to perform statistical analysis and generate Figure 5:
	•	rmsd_global_backbone.csv
	•	rmsd_motif_backbone.csv
	•	rmsf_global_CA.csv
	•	rmsf_motif_CA.csv
	•	rg_protein.csv
	•	sasa_motif_backbone.csv
	•	contacts_motif_vs_rest_0p45.csv
	•	mindist_motif_to_rest.csv
	•	water_within035_protein.csv
	•	water_within035_protein_noMotif.csv
	•	water_within035_motif_all.csv
	•	water_within035_motif_backbone.csv

---
Statistical processing and visualization were performed in R.

---

Data Availability
Raw trajectory files (.xtc, .trr) are not included due to file size constraints but can be regenerated using the provided input files and simulation parameters.
