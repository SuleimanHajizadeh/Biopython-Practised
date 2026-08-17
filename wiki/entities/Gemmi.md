---
title: Gemmi
type: entity
created: 2026-08-17
updated: 2026-08-17
tags:
  - structural-biology
  - mmcif
  - crystallography
  - ccd
sources:
  - "[[structural_biology/ProteinLigandAnalysis.ipynb]]"
---

# Gemmi

**Gemmi** is a modern, ultra-fast C++ library with Python bindings designed for structural biology, macromolecular crystallography, and mmCIF file processing.

---

## Use Cases in Repository

In `ProteinLigandAnalysis.ipynb`, Gemmi is used to parse the Chemical Component Dictionary (CCD) CIF documents and extract chemical SMILES strings directly from CIF loops.

### Parsing SMILES from Ligand CIF
```python
import gemmi

def parse_smiles_from_ligand_cif(cif_text: str) -> str:
    doc = gemmi.cif.read_string(cif_text)
    block = doc.sole_block()
    
    # Check for chem_comp_identifier loops
    loop = block.find(["_chem_comp_identifier.type", "_chem_comp_identifier.identifier"])
    for row in loop:
        if "SMILES" in row[0]:
            return row[1]
    return None
```

---

## Connections & See Also
- [[Bio.PDB]]: Standard Python parser for PDB/mmCIF hierarchy.
- [[RDKit]]: Converts the extracted SMILES into 2D/3D chemical structures.
- [[Protein-Ligand-Interaction-Profiling]]: The structural analysis pipeline.
