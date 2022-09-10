# Hackathon ASI 2022
 
## Overview

This repository contains scripts and generated data to assist in the [2022 ASI Systems Immunology Hackathon](https://www.immunology.org.au/events/2022-ASI-Systems-Immunology-SIG-Hackathon/). The challanges in the Hackathon are 

1. **Minimal cluster identification/marker extraction**: Identifying the ideal/minimal (i.e. 12-15) protein marker combinations to identify the maximal number of cell clusters based on RNA ± CITE-seq reference data set.
    + 1a Novel pipeline that allows extraction
    + 1b Utility: Lead to better panel choice for subsequent experiments
    + 1c Reference of rank order gene-protein correlation values (e.g. CD8 terrible with RNA, great with protein)
    + 1d Create minimal marker reference from dataset that can evolve for people to split into all immune subsets. Ala Simon Haas but better? Different?
    + 1e Novel biomarker identification from clinical cohorts
2. **Cell-cell, protein-protein interaction** (visualisation? More refined? Interpretation?)
    + 2a Don’t reinvent the great databases out there? Rather leverage these so immunologists can better use them
    + 3b Interfacing with the proteogenomics data
3. **Can we use RNA+protein references to inform genes likely to be expressed in FACS subsets? Vice versa?**
    + 3a Hopefully have a normalised reference FACS whole blood data set. Perhaps healthy vs COVID

## Paper and datasets

The datasets for this Hackathon are taken from two papers: [Liu_et_al_Cell_2021_COVID](https://doi.org/10.1016/j.cell.2021.02.018) and [Triana_et_al_Nat_Immunol_2021_Leukemia](https://doi.org/10.1038/s41590-021-01059-0). Instructions for downloading the data can be found in Angli's page [here](https://github.com/anglixue/asiosc_hackathon/tree/main/data).

## Code and generated data

I will be initially focusing on Challenge 1. The scripts are located in the `/src` folder. A brief description of the steps are as follows, focusing on the Adaptive dataset in Liu et al.

1. Split the gene expression data by batch and donor, and process and integrate the data using Seurat's [workflow](https://satijalab.org/seurat/articles/integration_introduction.html). The script can be found [here](https://github.com/raymondlouie/Hackathon-ASI-2022/blob/main/src/v1_integrate_gene_ref.Rmd) and output integrated Seurat object [here](https://www.dropbox.com/s/frp69o8sieq7t5g/integrated_seurat_gene_ref.rds?dl=0).
2. Split the protein data by batch and donor, and process and integrate the data using Seurat's [workflow](https://satijalab.org/seurat/articles/integration_introduction.html). The script can be found [here](https://github.com/raymondlouie/Hackathon-ASI-2022/blob/main/src/v1_integrate_protein.Rmd), and output integrated Seurat object [here](https://www.dropbox.com/s/saaylo7lo3v3l9n/integrated_seurat_protein.rds?dl=0).
3. Combine the integrated gene and protein matrices using Seurat's WNN [workflow](https://satijalab.org/seurat/articles/weighted_nearest_neighbor_analysis.html). The script can be found [here](https://github.com/raymondlouie/Hackathon-ASI-2022/blob/main/src/v2_merge_seurat_protein_gene_wnn.Rmd), and output integrated Seurat object [here](https://www.dropbox.com/s/90m94yrh02bv8et/wnn_integrated.RData?dl=0).

## Methods which choose optimal gene or protein markers

1. Paper: [Detection of cell markers from single cell RNA-seq with sc2marker](https://bmcbioinformatics.biomedcentral.com/articles/10.1186/s12859-022-04817-5). Tutorial and code (R): [Bioconductor/GitHub](https://github.com/CostaLab/sc2marker)
2. Paper: [geneBasis: an iterative approach for
unsupervised selection of targeted gene
panels from scRNA-seq](https://link.springer.com/content/pdf/10.1186/s13059-021-02548-z.pdf). Tutorial and code (R): [Bioconductor/GitHub](https://github.com/MarioniLab/geneBasisR)
3. Paper: [Optimal marker gene selection for cell type discrimination in single cell analyses](https://www.nature.com/articles/s41467-021-21453-4). Tutorial and code (Python): [Bioconductor/GitHub](https://github.com/solevillar/scGeneFit-python).
4. Paper: [CiteFuse enables multi-modal analysis of CITE-seq data](https://academic.oup.com/bioinformatics/article/36/14/4137/5827474). Tutorial and code (R): [Bioconductor/GitHub](https://www.bioconductor.org/packages/release/bioc/html/CiteFuse.html)

## Hackathon links

Angli's Hackathon [page](https://github.com/anglixue/asiosc_hackathon).

