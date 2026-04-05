# Biopython-Practised: Technical Implementations and Statistical Bio-computation

[![Biopython](https://img.shields.io/badge/Bioinformatics-Biopython-blue.svg)](https://biopython.org/)
[![Statistics](https://img.shields.io/badge/Statistics-ANOVA-orange.svg)](https://scipy.org/)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

## Overview

This repository contains an extensive collection of technical implementations and statistical methods utilized in biological data analysis. The project focuses on programmatic sequence manipulation, structural biology parsing, and advanced ANOVA-based statistical modeling for clinical and biological datasets.

---

## Technical Curriculum

The repository is structured into specific implementation domains:

### 1. Sequence Manipulation and Parsing
*   **Sequence Objects (Seq):** Modeling the Central Dogma with DNA, RNA, and protein conversions.
*   **File I/O (SeqIO):** Robust parsing of FASTA, GenBank, and FASTQ data formats.

### 2. NCBI Data Mining and Alignment
*   **Entrez Integration:** Programmatic retrieval of genomic data via NCBI APIs.
*   **Alignment Parsing (AlignIO):** Technical processing of PHYLIP, Stockholm, and Clustal alignments.
*   **ExPASy:** SwissProt database access and analysis.

### 3. Structural Bioinformatics
*   **PDB/CIF Parsing:** 3D coordinate analysis and structural metadata extraction via `Bio.PDB`.
*   **Ligand Interactions:** Quantification of spatial distances and interaction sites (Example: `1fat.cif`).
*   **Visualization:** Integration of PyMOL educational structures.

### 4. Statistical Bio-computation (ANOVA)
*   **Experimental Design:** One-way and multi-way ANOVA for drug-enzyme activity profiling.
*   **Tutorial Series:** Beginner to Advanced ANOVA tutorial notebooks focusing on F-distributions and interaction plots.

---

## Data Classification

Handled bioinformatics formats include:
- **Genomic:** FASTA (`.fa`, `.fna`), GenBank (`.gb`, `.gbk`).
- **Alignment:** Clustal (`.aln`), Stockholm (`.sth`), PHYLIP (`.phy`).
- **Structural:** PDB, CIF (`.cif`, `.bcif.gz`).
- **Sequencing:** FASTQ, SAM, BAM.

---

## Setup and Dependencies

Environment requirements for Jupyter Notebook execution:

```bash
pip install biopython pandas numpy scipy matplotlib seaborn
```

For structural biology analysis, a working installation of PyMOL is required.

---

## Usage Guide

1. **Clone the repository:**
   ```bash
   git clone https://github.com/SuleimanHajizadeh/Biopython-Practised.git
   ```
2. **Execute Modules:** Start with the fundamental lesson `Biopython 1ci ders.ipynb` and follow through to the advanced homework assignments.

---

## Contact

**Suleiman Hajizadeh**  
Lead Bioinformatician @ Azerbaijan  
- **Email:** suleyman.hacizade1@gmail.com  
- **Expertise:** Proteomics, Structural Bio-analysis, Statistics

---
> [!NOTE]
> All datasets utilized for training are sourced from NCBI, PDB, and official Biopython documentation archives.
