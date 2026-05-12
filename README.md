# 🐍 Biopython Implementation & Statistical Modeling Archive

[![Python](https://img.shields.io/badge/Python-3776AB?style=flat-square&logo=python&logoColor=white)](https://www.python.org/)
[![Biopython](https://img.shields.io/badge/Biopython-1.81-blue?style=flat-square)](https://biopython.org/)
[![Jupyter](https://img.shields.io/badge/Jupyter-Notebooks-F37626?style=flat-square&logo=jupyter&logoColor=white)](https://jupyter.org/)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg?style=flat-square)](https://opensource.org/licenses/MIT)

## 📌 Overview

This repository documents a **structured, 27+ lesson progression** through computational biology using Biopython, statistical modeling (ANOVA), protein-ligand analysis, and clinical data visualization. It serves as both a learning archive and a demonstration of systematic bioinformatics skill acquisition.

---

## 🗂️ Repository Structure

### 1. 🧬 Biopython Core Curriculum (Lessons 1–27+)

Structured Jupyter Notebooks covering the full Biopython ecosystem:

| Module | Topics Covered |
|--------|---------------|
| Fundamentals (1–6) | Sequence objects, transcription, translation, `SeqIO` |
| Data Mining (7–12) | NCBI Entrez, `AlignIO`, MSA parsing, GenBank records |
| Genomic Files (13–18) | FASTQ/FASTA/SAM/BED/PSL/Chain format handling |
| Structural Biology (19–24) | PDB/CIF parsing, protein structure (`1fat.cif`, `1gbt.bcif.gz`) |
| Advanced Topics (25–27+) | Metagenomics data, MERFISH single-cell, custom pipelines |

### 2. 📊 Statistical Modeling (ANOVA)

Multi-factorial statistical analysis notebooks:

| Notebook | Domain |
|---------|--------|
| `ANOVA_Drug_Enzyme_Activity_Project.ipynb` | Pharmacology — drug-enzyme kinetics |
| `Interaction_Plot_Clinical_Trial.ipynb` | Clinical trial — interaction effects |
| `Extended_ANOVA_Beginner_Project.ipynb` | Foundational statistical design |
| `Intermediate_ANOVA_Tutorial.ipynb` | Two-way ANOVA, post-hoc tests |
| `Advanced_ANOVA.ipynb` | Mixed models, repeated measures |

### 3. 🔬 Structural & Protein-Ligand Analysis

| Resource | Description |
|---------|-------------|
| `ProteinLigandAnalysis.ipynb` | Binding site analysis, docking visualization |
| `PyMOL/` | Molecular visualization scripts |
| `1fat.cif`, `1gbt.bcif.gz` | Real PDB crystal structure data |
| `2uvo_hhblits.hhr` | HHblits homology search results |

### 4. 🗺️ Sequence Alignment & Phylogenomics Files

| File | Type |
|------|------|
| `PF05371_seed.aln`, `adh.aln`, `W_prot.msf` | Multiple Sequence Alignments |
| `hg38.fa`, `ecoli.fa`, `bsubtilis.fa` | Reference genomes |
| `NC_005816.gb`, `EU490707.gbk` | GenBank records |
| `dna_rna.sam`, `ex1.sam` | Alignment (SAM format) |

---

## 🧰 Technical Stack

```
Python 3.x | Biopython | Pandas | NumPy | SciPy | Matplotlib | Seaborn | PyMOL
```

### Setup

```bash
pip install biopython jupyter pandas numpy scipy matplotlib seaborn
```

> Structural analysis modules require **PyMOL** (educational license). See `PyMOL/` directory.

---

## 🎓 Academic Context

This repository demonstrates systematic, self-directed acquisition of computational biology skills across sequence analysis, genomics, structural biology, and clinical statistics — directly relevant to graduate-level computational biology programs (e.g., MPhil Computational Biology, University of Cambridge).

---

**Author:** Suleiman Hajizadeh | Bioinformatician @ IMBB, Azerbaijan  
📧 suleyman.hacizade1@gmail.com
