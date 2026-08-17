---
title: Protein-Ligand Interaction Profiling
type: concept
created: 2026-08-17
updated: 2026-08-17
tags:
  - structural-biology
  - protein-ligand
  - binding-pocket
  - cheminformatics
sources:
  - "[[structural_biology/ProteinLigandAnalysis.ipynb]]"
---

# Protein-Ligand Interaction Profiling

**Protein-Ligand Interaction Profiling** combines macromolecular structural parsing with cheminformatics descriptors to evaluate binding poses, pocket compactness, and ligand drug-likeness.

---

## 1. Automated Workflow Pipeline

The pipeline implemented in `ProteinLigandAnalysis.ipynb` executes the following stages:

```
PDB mmCIF Fetch (RCSB API)
  ├── 1. Topology & Geometry (MDAnalysis)
  │     ├── Protein Radius of Gyration (Rg)
  │     └── Protein COM to Ligand COM Distance (Å)
  ├── 2. Sequence & Frequency (Bio.PDB PPBuilder)
  │     └── Amino Acid composition & length
  └── 3. Small Molecule Cheminformatics (Gemmi + RDKit)
        ├── Extract Ligand SMILES from wwPDB CCD
        └── Compute Lipinski / Physicochemical Descriptors
```

---

## 2. Structural Metrics

### Radius of Gyration ($R_g$)
Quantifies the spatial distribution of atoms around the protein's center of mass:

$$R_g = \sqrt{\frac{1}{M} \sum_i m_i (\mathbf{r}_i - \mathbf{r}_{COM})^2}$$

High $R_g$ indicates an extended or disordered conformation; low $R_g$ indicates a tightly folded, globular domain.

### Center of Mass (COM) Binding Distance
Measures the distance from the catalytic/global center of the receptor to the centroid of the bound small molecule:

$$d = \|\mathbf{r}_{COM}^{protein} - \mathbf{r}_{COM}^{ligand}\|$$

---

## 3. Cheminformatics Descriptors
- **Molecular Weight ($M_W$)**: Target $< 500 \text{ Da}$ (Lipinski's Rule of 5).
- **LogP (Octanol-Water Partition)**: Lipophilicity indicator (optimal $0 < \text{LogP} < 5$).
- **TPSA (Topological Polar Surface Area)**: Relates to cell permeability (optimal $< 140 \text{ \AA}^2$).

---

## Connections & See Also
- [[Bio.PDB]]: Structure parsing and polypeptide sequence extraction.
- [[Gemmi]]: Extracting ligand SMILES from wwPDB Chemical Component Dictionary.
- [[MDAnalysis]]: Computing $R_g$ and COM vectors.
- [[RDKit]]: Molecular descriptor generation.
