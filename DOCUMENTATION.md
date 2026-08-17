# 📖 Biopython & Biostatistics Complete Repository Documentation

This document provides a comprehensive technical reference for every directory, notebook, script, dataset, and knowledge artifact in the repository, along with an operational guide for using **Obsidian with the LLM Wiki pattern**.

---

## 📑 Table of Contents
1. [Repository Architecture](#1-repository-architecture)
2. [Directory & File Breakdown](#2-directory--file-breakdown)
   - [`biostatistics/` (Statistical Inference & ANOVA)](#biostatistics)
   - [`structural_biology/` (3D Modeling & Ligand Analysis)](#structural_biology)
   - [`practice_notebooks/` (Biopython Sequence & Alignment Exercises)](#practice_notebooks)
   - [`data/raw/` (Multi-Format Biological Datasets)](#dataraw)
   - [`presentations/` (Conceptual Slide Decks)](#presentations)
   - [`raw/` & `wiki/` (LLM Knowledge Graph Layer)](#raw--wiki)
3. [Obsidian + LLM Wiki: Architecture & Operational Guide](#3-obsidian--llm-wiki-architecture--operational-guide)
   - [The Human-Agent-Obsidian Triad](#the-human-agent-obsidian-triad)
   - [Graph View & Knowledge Navigation](#graph-view--knowledge-navigation)
   - [Standard Workflows (Ingest, Query, Lint)](#standard-workflows)

---

## 1. Repository Architecture

```
Biopython-Practised/
├── AGENTS.md                  # LLM Wiki Schema & Operational Guidelines
├── DOCUMENTATION.md           # Master technical repository reference (this file)
├── README.md                  # Project overview and badges
├── requirements.txt           # Python package dependencies
├── environment.yml            # Conda environment definition
├── hg38.chrom.sizes           # Human genome chromosome length reference
├── example.fastq copy         # Sample FASTQ read snippet
│
├── biostatistics/             # Statistical modeling & hypothesis testing notebooks
├── structural_biology/        # Protein 3D parsing, ligand descriptors, & Gradio app
├── practice_notebooks/        # Biopython sequence manipulation, MSA, BLAST notebooks
├── data/raw/                  # 26 standard bioinformatic data format files
├── presentations/             # Educational presentations on Biopython
│
├── raw/                       # Immutable user sources (papers, notes, transcripts)
│   └── assets/                # Downloaded media, figures, diagrams
│
└── wiki/                      # Living, interlinked LLM-maintained markdown knowledge base
    ├── index.md               # Master index catalog
    ├── log.md                 # Chronological changelog
    ├── entities/              # Specific tools, libraries, proteins, databases
    ├── concepts/              # Mechanisms, computational algorithms, protocols
    └── syntheses/             # Thematic deep-dives, comparisons, filed analyses
```

---

## 2. Directory & File Breakdown

### `biostatistics/`
Focuses on experimental variance analysis, hypothesis testing, and clinical trial modeling:

- **`ANOVA_Drug_Enzyme_Activity_Project.ipynb`**:
  - Simulates ALT (Alanine Aminotransferase) enzyme activity across 4 drug concentration regimes.
  - Computes one-way ANOVA $F$-statistic and performs pairwise post-hoc discrimination using **Tukey's HSD**.
- **`Advanced_ANOVA.ipynb` & `Advanced_ANOVA (1).ipynb`**:
  - Implements two-way ANOVA with interaction terms (`Treatment * Gender`).
  - Implements repeated measures ANOVA using `pingouin.rm_anova`.
  - Performs diagnostic assumption checks (Levene's test for homoscedasticity, Shapiro-Wilk for normality, Mauchly's sphericity).
- **`Extended_ANOVA_Beginner_Project.ipynb`**:
  - Pedagogical walkthrough explaining variance partitioning ($SS_{Total} = SS_{Between} + SS_{Within}$) with violin and boxplot visualizations.
- **`Interaction_Plot_Clinical_Trial.ipynb`**:
  - Visualizes biomarker responses across patient genotypes and drug dosage levels.
  - Teaches visual diagnosis of synergism vs antagonism in clinical data.
- **`Intermediate_ANOVA_Tutorial.ipynb`**:
  - Compares lightweight testing with `scipy.stats.f_oneway` against formula-based regression with `statsmodels.formula.api.ols` and `anova_lm(typ=2)`.

---

### `structural_biology/`
Integrates macromolecular structural biology with cheminformatics and interactive UI:

- **`ProteinLigandAnalysis.ipynb`**:
  - **Automated mmCIF Retrieval**: Downloads and caches `.cif` structures from RCSB wwPDB.
  - **SMILES Extraction via Gemmi**: High-performance parser extracting ligand SMILES from the Chemical Component Dictionary (CCD).
  - **Topology & Geometry via MDAnalysis**: Calculates protein Radius of Gyration ($R_g$), Center of Mass (COM) coordinates, and protein-ligand Euclidean COM distance vectors.
  - **Sequence Recovery via Bio.PDB**: Parses SMCRA hierarchy with `MMCIFParser` and reconstructs amino acid frequencies using `PPBuilder`.
  - **Cheminformatics via RDKit**: Computes Lipinski descriptors (Molecular Weight, LogP, TPSA, H-Bond Donors/Acceptors, Rotatable Bonds) and renders 2D molecular structures.
  - **Gradio Application**: Interactive web interface (`gradio_analyze`) wrapping the end-to-end pipeline.
- **`1fat.cif`**: mmCIF structural file for Legume Lectin complexed with carbohydrate.
- **`1gbt.bcif.gz`**: Gzipped BinaryCIF structure of G-protein $\beta\gamma$ subunit complex.
- **`2uvo_hhblits.hhr`**: HHblits profile-profile hidden Markov model homology search output against PDB70.
- **`pymol/`**: PyMOL visualization scripts and education licensing.

---

### `practice_notebooks/`
Hands-on exercises exploring Biopython APIs and modern best practices:

- **`1 dersCalisma.ipynb` & `firstHomeWork.ipynb`**:
  - `Bio.SeqIO.parse()` FASTA record iteration.
  - Sequence length and GC content calculation using `Bio.SeqUtils.gc_fraction`.
- **`2 dersCalisma.ipynb`, `Biopython ders 2.ipynb`, `2 dersCalisma(1).ipynb`**:
  - `Bio.Seq.Seq` vs `MutableSeq` mutability.
  - Transcription (`transcribe`), reverse transcription (`back_transcribe`), reverse complement (`reverse_complement`), and translation (`translate`).
  - NCBI Genetic Code codon tables (`Bio.Data.CodonTable`).
- **`four.ipynb`**:
  - Coordinate-matrix based alignment modeling (`Bio.Align.Alignment`, `Bio.Align.Alignments`).
  - Handling genomic interval tracks (`bigbed`, `PSL`).
- **`five.ipynb`**:
  - Pairwise dynamic programming with `Bio.Align.PairwiseAligner`.
  - Loading `BLOSUM62` substitution matrices with affine gap penalties.
  - Codon-aware alignment (`CodonAligner`) and McDonald-Kreitman tests (`mktest`).
- **`eight.ipynb`**:
  - Remote NCBI BLAST execution via `Bio.Blast.NCBIWWW.qblast`.
  - Parsing multi-hit BLAST XML records via `Bio.Blast.NCBIXML`.

---

### `data/raw/`
A library of 26 benchmark files representing fundamental bioinformatics data structures:

| Format Type | Extensions / Examples | Primary Use Case | Biopython / External Parser |
| :--- | :--- | :--- | :--- |
| **Sequences** | `alpha.faa`, `NC_005816.fna` | Unaligned amino acid / nucleotide records | `Bio.SeqIO` |
| **Rich Annotations** | `NC_005816.gb`, `EU490707.gbk` | Full GenBank gene features, CDS, and taxonomy | `Bio.SeqIO` |
| **Alignments** | `adh.aln`, `PF05371_seed.sth`, `PF05371_seed.phy` | ClustalW, Stockholm (Pfam), Phylip formats | `Bio.AlignIO` / `Bio.Align` |
| **Phylogenetics** | `codonposset.nex` | NEXUS phylogenetic tree/matrix | `Bio.Nexus` |
| **Genomic Intervals** | `bed12.bed`, `dna_rna.bb`, `dna_rna.psl` | UCSC genome browser intervals, BLAT output | `Bio.Align.bigbed`, `pybedtools` |
| **Genome Liftover** | `hg19ToHg38.chain`, `calJac3ToCalJac4.chain` | Coordinate mapping across assembly versions | `Bio.Align.chain` |
| **Comparative Genomes**| `combined.xmfa` | Mauve multiple whole-genome alignment | `Bio.AlignIO.MauveIO` |

---

### `presentations/`
- **`BioPython_DOC1.pptx`**: Slide presentation introducing biological sequence modeling, GC analysis, and `SeqRecord` attributes.
- **`BioPython_DOC2.pptx`**: Slide presentation covering multiple sequence alignments, BLAST, and database query workflows.

---

### `raw/` & `wiki/` (The Knowledge Graph)
- **`raw/`**: The immutable archive of source papers, clipped articles, and transcripts.
- **`wiki/index.md`**: Master catalog of the entire knowledge base.
- **`wiki/log.md`**: Chronological ledger of all agent activities.
- **`wiki/entities/`**: Dedicated pages for libraries and tools (`Bio.SeqIO`, `Bio.Seq`, `Bio.Align.PairwiseAligner`, `Bio.Align.Alignment`, `Bio.Blast`, `Bio.PDB`, `Gemmi`, `MDAnalysis`, `RDKit`, `statsmodels`, `pingouin`).
- **`wiki/concepts/`**: Conceptual deep-dives (`One-Way-ANOVA`, `Two-Way-ANOVA-and-Interaction`, `Repeated-Measures-ANOVA`, `Tukey-HSD-Post-Hoc`, `Pairwise-Sequence-Alignment`, `Multiple-Sequence-Alignment-Coordinates`, `Protein-Ligand-Interaction-Profiling`, `Central-Dogma-Sequence-Operations`, `Biological-Data-Formats`).
- **`wiki/syntheses/`**: Integrative theses (`Biopython-Modern-API-Migration`, `Computational-Biochemistry-and-Stats-Pipeline`, `Obsidian-LLM-Wiki-Integration`).

---

## 3. Obsidian + LLM Wiki: Architecture & Operational Guide

### The Human-Agent-Obsidian Triad

The **LLM Wiki Pattern** divides responsibilities between human, agent, and visual interface:

```
┌────────────────────────────────────────────────────────┐
│                        USER                            │
│  - Curates raw sources (papers, notes, links)          │
│  - Asks deep exploratory questions                     │
│  - Guides research direction                           │
└───────────────▲────────────────────────▲───────────────┘
                │                        │
        (Prompts & Queries)      (Browses Graph & Notes)
                │                        │
                ▼                        ▼
┌───────────────────────────┐    ┌───────────────────────┐
│         LLM AGENT         │    │       OBSIDIAN        │
│  - Reads & parses raw data│───▶│  - Visualizes Graph   │
│  - Writes wiki markdown   │    │  - Interactive Links  │
│  - Maintains cross-links  │    │  - Live Previews      │
│  - Updates Index & Log    │    │  - Backlink Explorer  │
└───────────────────────────┘    └───────────────────────┘
```

1. **Obsidian is the IDE**: Provides the graph view, live markdown rendering, link hovering, search, and backlink pane.
2. **The LLM is the Programmer / Maintainer**: Handles the reading, cross-referencing, entity updates, code extraction, and indexing.
3. **The Wiki is the Codebase**: A compounding, interconnected web of markdown files that grows more valuable over time.

---

### How to Use Obsidian With This Repository

1. **Open the Repository as a Vault**:
   - In Obsidian, click **"Open folder as vault"** and select `/Users/macbookairm2/Documents/GitHub/Biopython-Practised`.
2. **Explore the Graph View (`Cmd/Ctrl + G`)**:
   - Open Obsidian's **Graph View** to see all entities, concepts, and syntheses connected by real edges (`[[...]]`).
   - Notice the hub nodes like `[[Bio.Seq]]`, `[[Bio.PDB]]`, and `[[One-Way-ANOVA]]`.
3. **Start at `wiki/index.md`**:
   - Make `wiki/index.md` your home note. It catalogs every concept and entity with one-line summaries.
4. **Use Hover Previews (`Cmd/Ctrl + Hover`)**:
   - Hover over any `[[wikilink]]` inside Obsidian to read the target note without leaving your active document.
5. **Inspect Backlinks**:
   - Open the **Backlinks** side-panel in Obsidian to see every note that references your current page.

---

### Standard Workflows

#### 1. Ingesting New Material (`Ingest`)
- Drop a paper or markdown file into `raw/` (or paste text into chat).
- Tell the agent: *"Ingest this paper on enzyme kinetics."*
- The agent reads the source, updates relevant entity and concept pages, links new discoveries, updates `wiki/index.md`, and appends an entry to `wiki/log.md`.

#### 2. Asking Questions (`Query & Synthesize`)
- Ask complex multi-source questions: *"How does our structural ligand pipeline connect with our ANOVA assay results?"*
- The agent reads the wiki graph, synthesizes the answer with citations, and optionally files high-value answers into `wiki/syntheses/`.

#### 3. Health Checks (`Lint`)
- Ask the agent: *"Lint the wiki."*
- The agent checks for broken links, orphan pages with zero inbound links, and knowledge gaps.
