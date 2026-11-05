# Danuglipron atom count check - 5 Nov 2026
Checked by Muse, rerunning Masood's own notebook code (RDKit + Meeko, same SMILES, same seed 42).

SMILES (from glp1r_docking.ipynb, PubChem danuglipron PF-06882961):
C1CO[C@@H]1CN2C3=C(C=CC(=C3)C(=O)O)N=C2CN4CCC(CC4)C5=NC(=CC=C5)OCC6=C(C=C(C=C6)C#N)F

- Heavy atoms (no H): 41
- Formula: C31H30FN5O4 (31 C + 1 F + 5 N + 4 O = 41 heavy)
- Atoms with H added by RDKit: 71
- Original bound ligand in 7LCJ (RCSB, downloaded 5 Nov 2026): UK4, 41 HETATM lines, no hydrogens in the crystal file. 17 HOH water lines excluded.
- Meeko PDBQT from that RDKit molecule: 42 ATOM lines = 41 heavy + 1 polar H. The extra atom is ATOM 25, H, on the carboxylic acid OH (O24, charge -0.478).

So the 41 vs 42 gap is a hydrogen, not a heavy atom lost in docking. The input PDBQT has 42 lines, the original crystal ligand has 41 heavy atoms. Vina / the RMSD code comparing the two files counts them differently. This matches Aditya Soni's reply (implicit vs explicit hydrogen) and Phong Lam's point (docking does not change topology, check the input before docking).
Program: AutoDock Vina 1.2.5, ligand prepared RDKit ETKDG + MMFF, Meeko.
No RMSD was calculated, because the atom counts differ.
