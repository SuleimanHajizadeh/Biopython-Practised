---
title: RDKit
type: entity
created: 2026-08-17
updated: 2026-08-17
tags:
  - cheminformatics
  - small-molecules
  - molecular-descriptors
  - smiles
sources:
  - "[[structural_biology/ProteinLigandAnalysis.ipynb]]"
---

# RDKit

**RDKit** is the open-source toolkit for cheminformatics, machine learning on molecular graphs, and small-molecule property prediction.

---

## Use Cases in Repository

Used in `ProteinLigandAnalysis.ipynb` for calculating physicochemical descriptors and generating 2D depictions of bound co-factors/ligands.

### Molecular Descriptors Calculation
```python
from rdkit import Chem
from rdkit.Chem import Descriptors, Lipinski

def compute_descriptors(smiles: str) -> dict:
    mol = Chem.MolFromSmiles(smiles)
    if mol is None:
        return {"error": "Invalid SMILES"}
    
    return {
        "Molecular_Weight": round(Descriptors.MolWt(mol), 2),
        "LogP": round(Descriptors.MolLogP(mol), 2),
        "TPSA": round(Descriptors.TPSA(mol), 2),
        "H_Bond_Donors": Lipinski.NumHDonors(mol),
        "H_Bond_Acceptors": Lipinski.NumHAcceptors(mol),
        "Rotatable_Bonds": Lipinski.NumRotatableBonds(mol)
    }
```

---

## Connections & See Also
- [[Gemmi]]: Extracting ligand SMILES from the Chemical Component Dictionary.
- [[Protein-Ligand-Interaction-Profiling]]: Merging ligand descriptors with 3D structural metrics.
