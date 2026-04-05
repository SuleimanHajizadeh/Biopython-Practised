# Biopython-Practised: A Masterclass in Biological Data Manipulation

[![Biopython](https://img.shields.io/badge/Bioinformatics-Biopython-blue.svg)](https://biopython.org/)
[![Statistics](https://img.shields.io/badge/Statistics-ANOVA-orange.svg)](https://scipy.org/)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

## 📌 Project Overview

**Biopython-Practised** is a comprehensive repository dedicated to mastering the art of biological data manipulation and statistical bio-computation. It contains a curated set of Jupyter Notebooks, specialized Python scripts, and real-world biological datasets ranging from genomic sequences to 3D protein structures. 

Whether you are parsing **NCBI Entrez**, analyzing **ANOVA benchmarks** for drug-enzyme activity, or exploring **PyMOL** structures, this repository provides a rigorous learning pathway.

---

## 🧬 Curriculum & Syllabus

The repository is organized into distinct learning modules:

### 1. Fundamentals of Biopython
*   **Sequence Objects (`Seq`):** Handling DNA, RNA, and Protein sequences.
*   **Alphabet & Transcription:** Central Dogma modeling.
*   **File I/O (`SeqIO`):** Parsing FASTA, GenBank (GBK), and FASTQ formats.

### 2. Advanced Bio-Mining & Alignment
*   **NCBI Entrez:** Automated querying and downloading of genomic data.
*   **Multiple Sequence Alignment (`AlignIO`):** Working with PHYLIP, Stockholm (STH), and Clustal (ALN) files.
*   **SwissProt & ExPASy:** Programmatic access to curated protein databases.

### 3. Structural Bioinformatics
*   **PDB & CIF Parsing:** High-level analysis of 3D coordinates using `Bio.PDB`.
*   **Protein-Ligand Analysis:** Calculating distances and interaction sites (CIF Example: `1fat.cif`).
*   **Visual Integration:** PyMOL EDU integration for 3D visualization.

### 4. Statistical Bio-computation (ANOVA)
*   **Drug-Enzyme Interaction:** Evaluating clinical trial datasets.
*   **ANOVA Tutorials:** 
    - **Beginner:** Understanding variance and F-distributions.
    - **Intermediate:** Interaction plots and factorials.
    - **Advanced:** Multi-way ANOVA for complex biological experiments.

---

## 📊 Data Formats Supported

This repository provides hands-on practice for virtually all major bioinformatics file types:
- **Genomic:** FASTA (`.fa`, `.fna`, `.fasta`), GenBank (`.gb`, `.gbk`).
- **Alignment:** Clustal (`.aln`), Stockholm (`.sth`), PHYLIP (`.phy`), Nexus (`.nex`).
- **Sequencing:** FASTQ, SAM, BAM.
- **Structural:** PDB, CIF (`.cif`, `.bcif.gz`).
- **Metadata:** BED, GFF, Chain files.

---

## 🛠️ Installation & Setup

To replicate the notebooks, ensure you have a Python 3.x environment with the following dependencies:

```bash
pip install biopython pandas numpy scipy matplotlib seaborn
```

For **Structural Biology** modules, a PyMOL installation is recommended. An educational license (`pymol-edu-license.lic`) is included for qualified users in the `PyMOL/` directory.

---

## 🚀 How to Use

1. **Clone the repository:**
   ```bash
   git clone https://github.com/SuleimanHajizadeh/Biopython-Practised.git
   ```
2. **Launch Jupyter:**
   ```bash
   jupyter notebook
   ```
3. **Follow the Curriculum:** Start with `Biopython 1ci ders.ipynb` and proceed through the numerical homework files (e.g., `firstHomeWork.ipynb`).

---

## 📧 Contact

**Suleiman Hajizadeh**  
Lead Investigator @ Azerbaijan  
- **Email:** suleyman.hacizade1@gmail.com  
- **Topics:** Computational Biology, Statistical Analysis, Proteomics

---
> [!IMPORTANT]
> **Copyright Note:** This repository is for educational and practice purposes. Some data files are sourced from NCBI, PDB, and the Biopython documentation (e.g., `ls_orchid.fasta`).
