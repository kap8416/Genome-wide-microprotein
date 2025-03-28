# Human Microprotein Identification and Characterization Pipeline

## Overview
This repository provides a computational workflow for the identification and characterization of human microproteins (miPs). The pipeline integrates multiple analytical steps, including intrinsic disorder prediction, phylogenomic reconstruction, microprotein identification, expression profiling, and functional enrichment analysis.

<img width="796" alt="Screenshot 2025-03-27 at 10 21 34 PM" src="https://github.com/user-attachments/assets/96ecd260-fe01-4539-ba6a-1ff463e72510" />


## Workflow
### 1. Intrinsically Disordered Regions (IDRs) Prediction
- **Tool:** [IUPred2A](https://iupred2a.elte.hu/)
- **Method:** Prediction of IDRs using the "long disorder" mode.
- **Analysis:** Residues with disorder scores >0.5 were classified as disordered. Proteins with ≥30% disordered residues were considered intrinsically disordered, with ≥50% as highly disordered.
- **Statistical Analysis:** Wilcoxon rank-sum test (p < 0.05) to compare disorder fractions against known disordered proteins from [DisProt](https://www.disprot.org/).
- **Structural Modeling:** AlphaFold-based structural modeling to assess IDR localization.

### 2. Phylogenomic Reconstruction
- **Tool:** [REvolutionH-tl](https://biocomplexnet.github.io/GitHub.io/)
- **Input:** Filtered proteomes from Ensembl.
- **Process:**
  - Pairwise sequence alignments across species.
  - Orthogroup and paralog identification.
  - Event-labeled gene tree reconstruction.
  - Species tree inference and reconciliation.
- **Output:** Species tree files and visualization outputs.

### 3. Microprotein Identification
- **Tool:** [miPFinder2](https://github.com/ku-mip/mipfinder2)
- **Input:** UniProt and InterPro annotations.
- **Process:**
  - Identification of candidate miPs based on length and sequence conservation.
  - Functional characterization based on known protein domains and structural motifs.
- **Output:** Candidate miPs with functional annotations.

### 4. Expression Profiling
- **Database:** [GTEx](https://gtexportal.org/home/)
- **Process:**
  - miPs were categorized by tissue-specific expression and functional groups.
  - Statistical analysis of expression patterns across tissues.
- **Output:** Expression profiles with categorized miPs.

### 5. Functional Enrichment and Chromosomal Clustering
- **Tool:** [ShinyGO](http://bioinformatics.sdstate.edu/go/)
- **Process:**
  - GO term and pathway enrichment using hypergeometric tests (p < 0.05, FDR-adjusted).
  - Chromosomal clustering using a sliding window approach (window size = X kb, step size = Y kb).
- **Output:** Enriched GO terms, pathways, and chromosomal distribution of miPs.

## Installation and Usage
### Dependencies
Ensure the following tools and databases are installed:
- Python 3.x
- R (with Bioconductor packages)
- IUPred2A
- REvolutionH-tl
- miPFinder2
- GTEx database access
- ShinyGO


```

## Authors
Developed by Fernanda Román García and **[Katia Aviña Padilla](https://www.researchgate.net/profile/Katia-Avina-Padilla?ev=hdr_xprf&_tp=eyJjb250ZXh0Ijp7ImZpcnN0UGFnZSI6ImhvbWUiLCJwYWdlIjoiaG9tZSIsInBvc2l0aW9uIjoiZ2xvYmFsSGVhZGVyIn19)**.


## Citation
If you use this pipeline, please cite:
> Aviña-Padilla K. *Genome-wide Analysis of Human Microproteins: Evolutionary Stability of Core Regulators and Emergence of Adaptive Functions.* Under review.

---
For more details, please refer to the documentation and example datasets included in this repository.
