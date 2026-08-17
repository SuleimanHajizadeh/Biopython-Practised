---
title: MDAnalysis
type: entity
created: 2026-08-17
updated: 2026-08-17
tags:
  - structural-biology
  - molecular-dynamics
  - center-of-mass
  - radius-of-gyration
sources:
  - "[[structural_biology/ProteinLigandAnalysis.ipynb]]"
---

# MDAnalysis

**MDAnalysis** is an object-oriented Python library to analyze molecular dynamics simulations and macromolecular structure files (PDB, mmCIF, GRO, XTC, DCD).

---

## Use Cases in Repository

Used in `ProteinLigandAnalysis.ipynb` to calculate macromolecular topological metrics:

### 1. Universe Creation
```python
import MDAnalysis as mda

u = mda.Universe("structural_biology/1fat.cif")
protein = u.select_atoms("protein")
ligand = u.select_atoms("resname NAG")
```

### 2. Radius of Gyration ($R_g$)
Measures the compactness of the protein structure:
```python
rg = protein.radius_of_gyration()
print(f"Radius of Gyration: {rg:.2f} Å")
```

### 3. Center of Mass (COM) & Euclidean Distance
```python
import numpy as np

com_protein = protein.center_of_mass()
com_ligand = ligand.center_of_mass()

distance_com = np.linalg.norm(com_protein - com_ligand)
print(f"Protein COM - Ligand COM distance: {distance_com:.2f} Å")
```

---

## Connections & See Also
- [[Bio.PDB]]: Coordinate hierarchy and sequence extraction.
- [[Protein-Ligand-Interaction-Profiling]]: Comprehensive binding metrics.
