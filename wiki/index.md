# Wiki Index

Welcome to the LLM-maintained Knowledge Base. This index catalogs all concepts, entities, syntheses, and sources.

---

## 🏛 Entities
*Specific tools, libraries, proteins, databases, or organizations.*

- [[Bio.SeqIO|Bio.SeqIO]]: Standard interface for reading and writing FASTA, FASTQ, and GenBank files.
- [[Bio.Seq|Bio.Seq]]: String-like biological sequence objects, codon tables, translation, and transcription routines.
- [[Bio.Align.PairwiseAligner|Bio.Align.PairwiseAligner]]: Modern C-accelerated dynamic programming pairwise sequence aligner.
- [[Bio.Align.Alignment|Bio.Align.Alignment]]: Coordinate-matrix data structure representing sequence alignments.
- [[Bio.Blast|Bio.Blast]]: Programmatic NCBI BLAST query submission and XML output parser.
- [[Bio.PDB|Bio.PDB]]: Macromolecular 3D coordinate parser (PDB/mmCIF) with SMCRA hierarchy and PPBuilder.
- [[Gemmi|Gemmi]]: High-performance C++/Python mmCIF parser used for Chemical Component Dictionary (CCD) SMILES extraction.
- [[MDAnalysis|MDAnalysis]]: Molecular topology and trajectory analysis for radius of gyration and center-of-mass metrics.
- [[RDKit|RDKit]]: Cheminformatics toolkit for SMILES processing, molecular depiction, and Lipinski descriptor calculations.
- [[statsmodels|statsmodels]]: Statistical modeling package for OLS ANOVA formulas and Tukey HSD post-hoc testing.
- [[pingouin|pingouin]]: Experimental statistics toolkit for repeated measures ANOVA and sphericity testing.

---

## 💡 Concepts
*Mechanisms, computational algorithms, protocols, methodologies.*

- [[One-Way-ANOVA|One-Way ANOVA]]: Partitioning total variance into between-group and within-group sums of squares.
- [[Two-Way-ANOVA-and-Interaction|Two-Way ANOVA & Interaction]]: Multi-factor variance modeling and diagnosing synergy via interaction plots.
- [[Repeated-Measures-ANOVA|Repeated Measures ANOVA]]: Within-subject variance modeling and Mauchly's sphericity corrections.
- [[Tukey-HSD-Post-Hoc|Tukey's HSD Post-Hoc Test]]: Multiple comparison correction controlling Family-Wise Error Rate (FWER).
- [[Pairwise-Sequence-Alignment|Pairwise Sequence Alignment]]: Needleman-Wunsch global and Smith-Waterman local alignment dynamic programming.
- [[Multiple-Sequence-Alignment-Coordinates|MSA Coordinate Modeling]]: Modern gapless coordinate-matrix representation of biological alignments.
- [[Protein-Ligand-Interaction-Profiling|Protein-Ligand Interaction Profiling]]: Structural pocket compactness ($R_g$, COM distance) and small-molecule descriptors.
- [[Central-Dogma-Sequence-Operations|Central Dogma Sequence Operations]]: Programmatic translation, transcription, reading frames, and codon tables.

---

## 🔬 Syntheses & Theses
*Cross-cutting deep dives, comparisons, and filed query analyses.*

- [[Biopython-Modern-API-Migration|Biopython Modern API Migration Guide]]: Practical migration guide for legacy `pairwise2`, `GC`, and `Bio.Alphabet` patterns.
- [[Computational-Biochemistry-and-Stats-Pipeline|Computational Biochemistry & Statistics Integration Pipeline]]: The end-to-end research flow connecting sequence, structure, and statistical validation.

---

## 📚 Source Summaries
*Ingested source documents and their primary takeaways.*

- `biostatistics/*.ipynb`: Clinical trial and enzyme kinetics ANOVA modeling notebooks.
- `structural_biology/ProteinLigandAnalysis.ipynb`: End-to-end protein-ligand structural parsing and descriptor pipeline.
- `practice_notebooks/*.ipynb`: Hands-on training notebooks for Biopython core modules.
