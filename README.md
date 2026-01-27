# Exploring Immune Dysregulation in Depression Using RNA-seq

## Project overview
This project explores immune-related transcriptomic variation in depression using RNA-seq data from peripheral blood mononuclear cells (PBMCs).  
We focus on exploratory data analysis and unsupervised methods to investigate heterogeneity in gene expression rather than strict case–control comparisons.

The analysis is based on a publicly available dataset from the GEO database (GSE260603).

## Dataset
- **Source:** GEO (Gene Expression Omnibus)
- **Accession number:** GSE260603
- **Organism:** Homo sapiens
- **Data type:** RNA-seq
- **Tissue:** Peripheral blood mononuclear cells (PBMCs)
- **Samples:** Individuals with stress-related mental disorders and healthy controls

The original study applied a multi-omics approach combining RNA-seq, immune markers, and clinical variables.  
In this project, we focus only on the RNA-seq component for exploratory transcriptomic analysis.

## Analysis goals
The main objectives of this project are:
- to explore global transcriptomic variability in PBMC RNA-seq data,
- to investigate immune-related heterogeneity using dimensionality reduction methods,
- to identify gradual transcriptomic patterns rather than discrete clusters.

## Methods --> PLEASE UPDATE
The following methods were used in the analysis:
- data preprocessing and normalization (preprocessed data provided by the authors),
- Principal Component Analysis (PCA),
- analysis of PCA loadings to identify genes driving transcriptomic variation,
- construction of gene expression signatures based on top PCA loadings.

## Key observations --> PLEASE UPDATE
- PCA does not reveal clear separation between diagnostic groups.
- The observed variation likely reflects immune cell composition and immune activation.
- These findings are consistent with the original study, where immune-related subgroups emerged only after multi-omics integration.

 ## Requirements
- R (version ≥ 4.2 recommended)
- R packages:
  - readr
  - dplyr
  - ggplot2 (optional)
  - uwot
  - biomaRt

## Authors
- Jan Rysiak  
- Ihor Mokrytskyi  
- Maya Śliwa
