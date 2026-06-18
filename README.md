# 🐍 Biopython & Biostatistics Practice Portfolio

[![Python](https://img.shields.io/badge/Python-3776AB?style=flat-square&logo=python&logoColor=white)](https://www.python.org/)
[![Biopython](https://img.shields.io/badge/Library-Biopython-blue.svg?style=flat-square)](https://biopython.org/)
[![Statistics](https://img.shields.io/badge/Focus-Biostatistics_|_ANOVA-orange.svg?style=flat-square)](https://www.statsmodels.org/)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg?style=flat-square)](https://opensource.org/licenses/MIT)

## 📌 Overview

This repository compiles practical notebooks and coding exercises in **computational biology, biostatistics, and structural bioinformatics**. It represents a hands-on training log focusing on programmatic sequence manipulation, statistical validation of biochemical data, and molecular modeling.

---

## 🗂️ Repository Structure

Designed for easy tracking and clean modularity:

```
Biopython-Practised/
├── requirements.txt            # Python package dependencies
├── environment.yml             # Conda environment definition
├── .gitignore                  # Git untracked pattern file
├── LICENSE
├── README.md
│
├── biostatistics/              # Statistical modeling of experimental data
│   ├── ANOVA_Drug_Enzyme_Activity_Project.ipynb  # One-way & Two-way ANOVA on drug actions
│   ├── Advanced_ANOVA.ipynb                      # Multi-factor ANOVA models
│   ├── Extended_ANOVA_Beginner_Project.ipynb     # Step-by-step variance analysis
│   ├── Interaction_Plot_Clinical_Trial.ipynb     # Multi-variable interaction plots
│   └── Intermediate_ANOVA_Tutorial.ipynb         # Diagnostics & post-hoc tests (Tukey's HSD)
│
├── structural_biology/         # Protein structural modeling and parsing
│   ├── ProteinLigandAnalysis.ipynb               # 3D structure parsing & ligand binding pocket metrics
│   ├── 1fat.cif / 1gbt.bcif.gz                   # PDB macromolecular structures
│   └── pymol/                                    # PyMOL education license
│
├── practice_notebooks/         # Sequence analysis exercises
│   └── [1-18]_HomeWork.ipynb   # Hand-on training covering SeqIO, NCBI Entrez, AlignIO, etc.
│
├── data/                       # Local database files
│   └── raw/                    # Raw FASTA, SAM, BAM, BED, chain, and TSV files
│
└── presentations/              # Conceptual lecture slides
    ├── BioPython_DOC1.pptx     # Principles of Biopython Seq & Align modules
    └── BioPython_DOC2.pptx     # Multiple Sequence Alignments and database queries
```

---

## 🔬 Core Themes

### 1. 📊 Biostatistics (ANOVA & Clinical Data Diagnostics)
*   **One-Way & Two-Way ANOVA:** Quantitative analysis of drug treatment effects on enzyme activity.
*   **Post-hoc Testing:** Pairwise comparisons using Tukey's HSD (Honestly Significant Difference) and Bonferroni corrections.
*   **Interaction Plots:** Visualizing synergism/antagonism in multi-factor clinical trials.

### 2. 🧬 Structural Biology & Ligand Interactions
*   Parsing PDB and CIF files using Biopython's `PDB` parser to extract coordinates and analyze geometry.
*   Determining protein-ligand binding properties, calculating spatial distance vectors, and visualizing models in PyMOL.

### 3. 💾 Sequence Analysis Practice
*   **SeqIO:** Reading and writing FASTA/FASTQ/GenBank file formats.
*   **NCBI Entrez:** Querying GenBank databases programmatically using E-utilities.
*   **AlignIO:** Parsing Multiple Sequence Alignments (MSA) and computing Jukes-Cantor/Kimura evolutionary distance matrices.

---

## 🔬 Mathematical & Statistical Foundations

To validate biochemical assays and clinical drug responses, the biostatistics pipelines in this repository utilize the following mathematical frameworks:

### 1. Analysis of Variance (ANOVA)
To test whether $k$ independent group means are significantly different, we compute the $F$-ratio of the between-group variance to the within-group variance:
$$F = \frac{\text{Mean Square Between (MSB)}}{\text{Mean Square Within (MSW)}} = \frac{SS_{\text{between}} / (k - 1)}{SS_{\text{within}} / (N - k)}$$
where:
* $SS_{\text{between}} = \sum_{j=1}^{k} n_j (\bar{Y}_j - \bar{Y})^2$ represents the variation among group means.
* $SS_{\text{within}} = \sum_{j=1}^{k} \sum_{i=1}^{n_j} (Y_{ij} - \bar{Y}_j)^2$ represents the residual variation within groups.
* $N$ is the total sample size across all groups.

---

### 2. Tukey's Honestly Significant Difference (HSD)
When the ANOVA $F$-test rejects the null hypothesis, post-hoc pairwise comparisons are performed to control the Family-Wise Error Rate (FWER). The minimum significant difference between any two group means is defined as:
$$\text{HSD} = q_{\alpha, k, N-k} \sqrt{\frac{\text{MSW}}{n}}$$
where $q$ is the Studentized Range distribution critical value at significance level $\alpha$, and $n$ is the sample size per group (assuming a balanced design).

---

## 🔗 Related Portfolios

This repository is part of a comprehensive bioinformatics research profile:

| Scale | Repository | Focus |
|-------|------------|-------|
| **Core Methodology Hub** | [Bioinformatics](https://github.com/SuleimanHajizadeh/Bioinformatics) | Cambridge ML Math · Biopython Curriculum · Metagenomics |
| **Transcriptomics & Oncology** | [Bioinformatics-analysis](https://github.com/SuleimanHajizadeh/Bioinformatics-analysis) | RNA-seq · TNBC · Clinical genomics pipelines |
| **Structural Biology (3D Protein AI)** | [computational-structural-biology](https://github.com/SuleimanHajizadeh/computational-structural-biology) | AKT1/STN7 kinase modeling & molecular docking |
| **Phylogenomics & Evolution** | [MEGA-Software-Genetics](https://github.com/SuleimanHajizadeh/MEGA-Software-Molecular-Evolutionary-Genetics-Analysis) | COL1A1 multi-species sequence alignment |

---

**Author:** Suleiman Hajizadeh | Bioinformatician @ IMBB, Azerbaijan  
📧 suleyman.hacizade1@gmail.com | 🔗 [GitHub Portfolio](https://github.com/SuleimanHajizadeh)
 