# Exploring Immune Dysregulation in Depression Using RNA-seq

## Project overview
This project explores immune-related transcriptomic variation in depression using RNA-seq data from peripheral blood mononuclear cells (PBMCs).  
We focus on exploratory data analysis and unsupervised methods to investigate heterogeneity in gene expression rather than strict case–control comparisons.

The analysis is based on a publicly available dataset from the GEO database (GSE260603).

## Introduction
The contemporary world, with its financial inequalities, employment instability, and global crises such as climate change or the pandemic, creates a favorable environment for the development of affective disorders (Ridley et al., 2020). Within just the first two decades of the 21st century, the number of people suffering from depression increased by nearly 60%, underscoring the need for a deeper understanding of this disorder and its etiology in order to effectively address the growing mental health crisis (Abbafati et al., 2020).

According to the ICD-11 classification, the diagnosis of a depressive episode requires the presence of at least five symptoms, one of which must belong to the affective cluster (Gałecki & Szulc, 2023). Additional symptoms include difficulties with concentration and memory, extremely low self-esteem, inappropriate feelings of guilt, sleep and appetite disturbances, as well as suicidal thoughts or behaviors. The ICD-11 classification also allows for the specification of symptom severity and the presence of psychotic features, which is crucial when deciding whether pharmacological treatment should be initiated.

The inflammatory theory of depression postulates that chronic inflammation in the body affects brain function, leading to the development of depressive symptoms. In individuals with depression, elevated levels of cytokines (interleukin-6, tumor necrosis factor alpha, interleukin-1 beta) are frequently observed; these cytokines can cross the blood–brain barrier and influence microglial activation (Paul et al., 2022). Immune cells residing in the brain produce reactive oxygen species and nitric oxide, resulting in neurotoxicity. An important role is also played by tryptophan metabolism—cytokines activate indoleamine-pyrrole 2,3-dioxygenase (IDO) and tryptophan 2,3-dioxygenase (TDO), which promote metabolic pathways leading to the production of kynurenine instead of serotonin. Kynurenine is subsequently converted into the neurotoxic quinolinic acid, which activates N-methyl-D-aspartate (NMDA) receptors, leading to excessive neuronal excitation and neuronal death (Paul et al., 2022).

## Dataset
- **Source:** GEO (Gene Expression Omnibus)
- **Accession number:** GSE260603
- **Organism:** Homo sapiens
- **Data type:** RNA-seq
- **Tissue:** Peripheral blood mononuclear cells (PBMCs)
- **Samples:** Individuals with stress-related mental disorders and healthy controls

The original study applied a multi-omics approach combining RNA-seq, immune markers, and clinical variables.  
In this project, we focus only on the RNA-seq component for exploratory transcriptomic analysis.

## Differential expression analysis
Differential expression analysis revealed that the upregulated gene set was dominated by non-coding transcripts, including long non-coding RNAs (lncRNAs), Y RNAs, and several transcribed pseudogenes (e.g. PRKY, ANOS2P, TXLNGY). Most of these transcripts are poorly characterized and lack evidence for protein-coding potential or involvement in known biological pathways.

In contrast, the downregulated genes included protein-coding genes associated with cytoskeletal organization (MAP7D2), regulation of protein phosphatase activity (PPP1R2C), and cell cycle–related processes such as mitotic spindle control and chromatid segregation (ERCC6L). Additionally, two key long non-coding RNAs involved in X-chromosome inactivation, TSIX and XIST, were significantly downregulated.

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

## Bibliography
Abbafati, C., Abbas, K. M., Abbasi, M., Abbasifard, M., Abbasi-
Kangevari, M., Abbastabar, H., Abd-Allah, F., Abdelalim, A., Abdollahi,
M., Abdollahpour, I., Abedi, A., Abedi, P., Abegaz, K. H., Abolhassani,
H., Abosetugn, A. E., Aboyans, V., Abrams, E. M., Abreu, L. G., Abrigo,
M. R. M., … Murray, C. J. L. (2020). Global burden of 369 diseases and
injuries in 204 countries and territories, 1990–2019: a systematic analysis
for the Global Burden of Disease Study 2019. The Lancet, 396(10258),
1204–1222. https://doi.org/10.1016/S0140-6736(20)30925-9

Gałecki, P., & Szulc, A. (2023). Psychiatria. Rozpoznania według ICD-11.
(Vol. 1). Edra Urban & Partner.

Paul, E. R., Schwieler, L., Erhardt, S., Boda, S., Trepci, A., Kämpe, R.,
Asratian, A., Holm, L., Yngve, A., Dantzer, R., Heilig, M., Hamilton, J.
P., & Samuelsson, M. (2022). Peripheral and central kynurenine pathway
abnormalities in major depression. Brain, Behavior, and Immunity, 101,
136–145. https://doi.org/10.1016/j.bbi.2022.01.002

Ridley, M., Rao, G., Schilbach, F., & Patel, V. (2020). Poverty, depression,
and anxiety: Causal evidence and mechanisms. In Science (Vol. 370, Issue
6522). American Association for the Advancement of Science.
https://doi.org/10.1126/science.aay0214
