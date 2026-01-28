# Exploring Immune Dysregulation in Depression Using RNA-seq

## Project overview
This project explores immune-related transcriptomic variation in depression using RNA-seq data from peripheral blood mononuclear cells (PBMCs). We focus on exploratory data analysis and unsupervised methods to investigate heterogeneity in gene expression rather than strict case–control comparisons.

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

The original study applied a multi-omics approach combining RNA-seq, immune markers, and clinical variables. In this project, we focus only on the RNA-seq component for exploratory transcriptomic analysis.

## Differential expression analysis
Differential expression analysis revealed that the upregulated gene set was dominated by non-coding transcripts, including long non-coding RNAs (lncRNAs), Y RNAs, and several transcribed pseudogenes (e.g. PRKY, ANOS2P, TXLNGY). Most of these transcripts are poorly characterized and lack evidence for protein-coding potential or involvement in known biological pathways.

In contrast, the downregulated genes included protein-coding genes associated with cytoskeletal organization (MAP7D2), regulation of protein phosphatase activity (PPP1R2C), and cell cycle–related processes such as mitotic spindle control and chromatid segregation (ERCC6L). Additionally, two key long non-coding RNAs involved in X-chromosome inactivation, TSIX and XIST, were significantly downregulated.

## Analysis goals
The main objectives of this project are:
- to explore global transcriptomic variability in PBMC RNA-seq data,
- to investigate immune-related heterogeneity using dimensionality reduction methods,
- to identify gradual transcriptomic patterns rather than discrete clusters.

## Methods
The following methods were used in the analysis:
- data preprocessing and normalization (preprocessed data provided by the authors),
- Principal Component Analysis (PCA),
- analysis of PCA loadings to identify genes driving transcriptomic variation,
- construction of gene expression signatures based on top PCA loadings.
- gene set annotation: immunologic gene sets (MSigDB category C7) were retrieved using the msigdbr package; gene sets were restricted to Homo sapiens and mapped using Ensembl gene IDs.
- background gene universe: a background gene list was defined from normalized RNA-seq expression data (GSE260603_normalized_data.tsv).
- enrichment analysis: over-representation analysis was performed using clusterProfiler::enricher(); upregulated and downregulated gene sets were analyzed independently.

## Figures 
<img width="590" height="450" alt="Screenshot 2026-01-28 at 21 38 59" src="https://github.com/user-attachments/assets/4706e4aa-082d-4ccf-93de-7288f05a8b68" />

Figure 1. Sex distribution across affected and control groups

The figure presents the number of female and male samples in the affected and control groups. The affected group contains a substantially higher number of samples than the control group, with females being overrepresented in both groups. This unequal group size and sex distribution were considered during interpretation of downstream analyses.

<img width="590" height="434" alt="Screenshot 2026-01-28 at 21 39 07" src="https://github.com/user-attachments/assets/7e984992-2fef-40d8-9511-e69cd65f07fd" />

Figure 2. PCA of gene expression data with samples colored by gender, affected status, BMI, and age

Principal component analysis (PCA) was performed on normalized gene expression data to assess global sources of variation across samples. Samples were colored according to gender, affected status, body mass index (BMI), and age. No clear separation of samples was observed along the first two principal components with respect to any of the examined variables, indicating that the main axes of transcriptomic variation are not driven by these demographic or clinical factors.

<img width="528" height="434" alt="Screenshot 2026-01-28 at 21 39 34" src="https://github.com/user-attachments/assets/7aa33800-4a3c-4798-99a5-14d86508b583" />

Figure 3. Volcano plot showing differential gene expression between affected and control samples

The volcano plot summarizes the results of differential gene expression analysis comparing affected and control samples. Each point represents a gene, plotted by log2 fold change (log2FC) on the x-axis and statistical significance expressed as −log10(adjusted p-value) on the y-axis. Genes passing the significance thresholds (|log2FC| > 1 and adjusted p-value < 0.01) are highlighted, with upregulated genes shown in red and downregulated genes in blue, while non-significant genes are shown in grey. This visualization highlights a subset of genes exhibiting strong and statistically significant expression changes between the two groups.

<img width="528" height="363" alt="Screenshot 2026-01-28 at 21 39 51" src="https://github.com/user-attachments/assets/dd220897-49ff-4b2c-abcd-8e06f189fab1" />

Figure 4. Proportion of affected and control samples across clusters identified by unsupervised clustering

The bar plot shows the proportion of affected and control samples within each cluster identified by unsupervised clustering. Both clusters are dominated by affected samples, with only a small proportion of control samples present in each cluster. While slight differences in the relative contribution of control samples between clusters can be observed, no cluster is exclusively associated with either affected or control status.

<img width="1344" height="960" alt="621071802_3104116599788698_3732104398971349286_n" src="https://github.com/user-attachments/assets/d418c3d3-2d1e-42e1-8b4c-0018a4ecb904" />

Figure 5. PCA of normalized gene expression data with samples colored by gender, affected status, BMI, and age

Principal component analysis (PCA) was performed on normalized gene expression data to assess global sources of variation across samples. Samples were colored according to gender, affected status, body mass index (BMI), and age. No clear separation of samples was observed along the first two principal components with respect to any of the examined variables, indicating that the main axes of transcriptomic variation are not driven by these demographic or clinical factors.

<img width="1344" height="960" alt="619960021_942029334862976_5741874887499253879_n" src="https://github.com/user-attachments/assets/98033ab0-9987-43f2-92d2-66272b264dac" />

Figure 6. Dispersion estimates as a function of mean normalized counts, showing gene-wise estimates, fitted trend, and final shrunk dispersions used by DESeq2.

The plot shows the relationship between gene-wise dispersion estimates and the mean of normalized counts as estimated by DESeq2. Black points represent raw gene-wise dispersion estimates, the red line indicates the fitted dispersion trend, and blue points show the final dispersion estimates after empirical Bayes shrinkage. As expected, dispersion decreases with increasing mean expression, and shrinkage stabilizes dispersion estimates for lowly expressed genes. These final dispersion estimates were used in downstream differential expression analysis.

<img width="1344" height="960" alt="624831943_867901589370304_4639917354214700540_n" src="https://github.com/user-attachments/assets/169e2fcc-7a07-4b6a-8582-0b1e16494e0e" />

Figure 7. Distribution of BMI and age across the study cohort.

The histograms show the distribution of body mass index (BMI) and age across all samples included in the analysis. BMI values are concentrated in the range typical for adult populations, with a right-skewed distribution and a small number of higher values. Age shows a broader distribution, spanning young to older adults, reflecting the heterogeneity of the study cohort. These variables were considered as potential covariates in downstream analyses.

## Key observations 
- PCA does not reveal clear separation between diagnostic groups.
- The observed variation likely reflects immune cell composition and immune activation.
- These findings are consistent with the original study, where immune-related subgroups emerged only after multi-omics integration.
- Enrichment analysis using MSigDB C7 immunologic gene sets revealed distinct transcriptional patterns between severe and healthy samples.
- Upregulated genes were predominantly non-coding transcripts, including lncRNAs, Y RNAs, and transcribed pseudogenes, most of which lack functional annotation in known immune pathways. This suggests that disease-associated transcriptional activation may involve regulatory or poorly characterized RNA mechanisms rather than classical protein-coding immune responses.
- Downregulated genes included protein-coding genes involved in cytoskeletal organization, phosphatase regulation, and cell cycle–related processes.
- The long non-coding RNAs XIST and TSIX, key regulators of X-chromosome inactivation, were significantly downregulated, indicating potential disruption of epigenetic regulation in the severe group.

 ## Requirements
- R (version ≥ 4.2 recommended)
- R packages:
  - readr
  - dplyr
  - ggplot2 (optional)
  - uwot
  - tidyverse
  - biomaRt
  - clusterProfiler
  - msigdbr

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
