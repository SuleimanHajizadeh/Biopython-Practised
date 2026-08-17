---
title: Bio.PDB
type: entity
created: 2026-08-17
updated: 2026-08-17
tags:
  - biopython
  - structural-biology
  - pdb
  - mmcif
  - coordinates
sources:
  - "[[structural_biology/ProteinLigandAnalysis.ipynb]]"
---

# Bio.PDB

`Bio.PDB` is Biopython's macromolecular 3D structure parsing, modeling, and geometry calculation module.

---

## SMCRA Hierarchy

Biopython organizes structural data into the **SMCRA** (Structure $\rightarrow$ Model $\rightarrow$ Chain $\rightarrow$ Residue $\rightarrow$ Atom) object model:

```
Structure (id)
  └── Model (0, 1, ...)
        └── Chain ('A', 'B', ...)
              └── Residue (resname, id, hetflag)
                    └── Atom (name, coord, b_factor)
```

---

## Parsing mmCIF and Extracting Sequences

```python
import Bio.PDB
from Bio.PDB import MMCIFParser, PPBuilder

parser = MMCIFParser(QUIET=True)
structure = parser.get_structure("1FAT", "structural_biology/1fat.cif")

# Extract polypeptide sequences
ppb = PPBuilder()
for pp in ppb.build_peptides(structure):
    seq = pp.get_sequence()
    print(f"Polypeptide Sequence ({len(seq)} AA): {seq[:30]}...")
```

---

## Geometric & Spatial Calculations

```python
# Calculate distance between two atoms
atom1 = structure[0]["A"][10]["CA"]
atom2 = structure[0]["A"][25]["CA"]
distance = atom1 - atom2  # Euclidean distance in Angstroms (Å)
print(f"C-alpha distance: {distance:.2f} Å")
```

---

## Connections & See Also
- [[Gemmi]]: High-performance modern parser for complex CIF loops and CCD data.
- [[MDAnalysis]]: Used for molecular dynamics coordinates and radius of gyration.
- [[Protein-Ligand-Interaction-Profiling]]: Full workflow integrating Bio.PDB with cheminformatics.
