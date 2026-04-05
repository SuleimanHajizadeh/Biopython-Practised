# Biopython Implementation and Statistical Modeling Archive

[![Biopython](https://img.shields.io/badge/Bioinformatics-Biopython-blue.svg)](https://biopython.org/)
[![Statistics](https://img.shields.io/badge/Statistics-ANOVA-orange.svg)](https://scipy.org/)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

## Overview

This repository contains the technical implementations and statistical bio-computation workflows utilized in genomic and structural data analysis. The project is focused on programmatic biological data manipulation via Biopython and factor-based statistical modeling (ANOVA) for clinical trial datasets.

---

## Technical Curriculum and Assignments

The learning and implementation pathway is organized into structured modules and homework assignments:

### 1. Biopython Marathon (1–30)
Technical Jupyter Notebooks focusing on the programmatic handling of biological sequences:
- **Baseline Fundamentals:** `Biopython 1ci ders.ipynb` and `Biopython ders 2.ipynb`.
- **Homework Progression:** Sequential assignments from `firstHomeWork.ipynb` to `eighteenthHomeWork.ipynb`, covering transcription, translation, and file I/O (SeqIO/AlignIO).
- **Seminars:** `Biopython ders 2 seminar.ipynb` - Deep dive into sequence alignment and NCBI Entrez querying.

### 2. Statistical Modeling (ANOVA)
Specialized notebooks for multi-factorial biological data analysis:
- **Drug and Enzyme Activity:** `ANOVA_Drug_Enzyme_Activity_Project.ipynb`.
- **Clinical Trials:** `Interaction_Plot_Clinical_Trial.ipynb`.
- **Methodology Tutorials:** 
    - `Extended_ANOVA_Beginner_Project.ipynb`.
    - `Intermediate_ANOVA_Tutorial.ipynb`.
    - `Advanced_ANOVA.ipynb`.

### 3. Structural and Genomic Data Files
The repository includes real-world data indices for structural parsing:
- **PDB/CIF Data:** `1fat.cif`, `1gbt.bcif.gz`, and `2uvo_hhblits.hhr`.
- **Genomic Indices:** `ecoli.fa`, `bsubtilis.fa`, `NC_005816.gb`, and `drosophila.fasta`.
- **Sequencing:** `example.fastq`, `dna_rna.sam`, and `est.panTro5.psl`.

---

## Technical Stack

- **Python Core:** Biopython, Scipy (Stats), Pandas, Numpy.
- **Visualization:** Matplotlib, Seaborn, PyMOL.
- **Analysis:** Jupyter Notebook (IPYNB).

---

## Laboratory Setup

### Environment Dependencies:

```bash
pip install biopython jupyter pandas numpy scipy matplotlib
```

Structural modules (PDB/CIF) require a working installation of **PyMOL**. Educational license metadata is available in the `PyMOL/` directory.

---

## Author Contact

**Suleiman Hajizadeh**  
Lead Bioinformatician @ Azerbaijan  
- **Email:** suleyman.hacizade1@gmail.com  
- **Topics:** Advanced Proteomics, Structural Bio-analysis, Statistics

---
> [!NOTE]
> All biological data used (e.g., `ls_orchid.fasta`, `hg38.fa`) are sourced from public archival databases (NCBI/PDB). Refer to the `documents/` directory for additional reference metadata.
