# RNA-seq Analysis of GSE236155

RNA-seq analysis of the publicly available **GSE236155** dataset using R and Bioconductor.

This project was completed as part of the **Functional Genomic Technologies** course during the MSc Bioinformatics programme at the University of Edinburgh. The analysis was developed from an R Markdown template provided by **Prof. Simon Tomlinson** and was adapted for GSE236155, with dataset-specific processing, visualization, downstream analysis and interpretation.

## Overview

The analysis compares two experimental groups:

* **NC** – control samples
* **OE** – overexpression samples

The dataset contains six mouse RNA-seq samples, with three biological replicates in each group.

The workflow includes:

* preparation of sample metadata
* filtering of low-count genes
* library-size normalisation using DESeq2
* comparison of expression-data transformations
* exploratory analysis using PCA and sample-distance heatmaps
* differential gene-expression analysis with DESeq2
* annotation of Ensembl gene identifiers using `biomaRt`
* visualisation of differential expression using MA plots, heatmaps and volcano plots
* examination of genes highlighted in the original study
* gene-set enrichment analysis using `fgsea`
* investigation of enriched Hallmark pathways and leading-edge genes

## Analysis workflow

### 1. Data preparation

The supplied count matrix is converted into a `DESeqDataSet`, together with sample metadata describing the experimental condition.

Genes with very low read counts are removed prior to downstream analysis.

### 2. Normalisation and exploratory analysis

DESeq2 size factors are estimated to account for differences in sequencing depth between samples.

Several transformations are explored, including:

* log-transformed normalised counts
* fragments per million (FPM)
* variance-stabilising transformation (VST)
* regularised log transformation (rlog)

Sample relationships are assessed using:

* principal component analysis (PCA)
* pairwise sample distances
* sample-distance heatmaps

### 3. Differential expression

Differential expression between the **OE** and **NC** groups is tested using **DESeq2**.

The analysis generates:

* log2 fold changes
* Wald statistics
* raw p-values
* multiple-testing-adjusted p-values

Differential-expression results are explored using MA plots, heatmaps and ranked result tables.

### 4. Gene annotation

Ensembl gene identifiers are mapped to gene names and additional annotation using the `biomaRt` package.

Annotated results are then used for downstream visualisation and biological interpretation.

### 5. Visualisation

The analysis includes:

* PCA plots
* sample-distance heatmaps
* differential-expression heatmaps
* MA plots
* volcano plots

A set of genes discussed in the original study is highlighted for comparison with the results of this reanalysis.

### 6. Gene-set enrichment analysis

Genes are ranked using the DESeq2 Wald statistic and analysed with **fgsea**.

Hallmark gene sets are used to identify pathways enriched toward either end of the ranked gene list.

The analysis includes:

* enrichment plots for selected pathways
* tables of highly enriched pathways
* comparison of positively and negatively enriched pathways
* collapsed pathway results
* examination of leading-edge genes from selected pathways

## Main tools and packages

The analysis is primarily performed in **R** using:

* `DESeq2`
* `Bioconductor`
* `biomaRt`
* `fgsea`
* `EnhancedVolcano`
* `pheatmap`
* `ggplot2`
* `dplyr`
* `edgeR`
* `limma`

Package and R version information can be reproduced using the `sessionInfo()` output included at the end of the analysis.

## Data availability

The RNA-seq experiment analysed here is publicly available through NCBI GEO under accession:

**GSE236155**

The object used as the starting input for the original coursework analysis, `mytable_feaures`, contained STAR aligned count and annotation data prepared by **Prof. Simon Tomlinson** for the Functional Genomic Technologies course.

**This course-provided object is not distributed in this repository.**

Users wishing to reproduce the analysis independently should obtain the corresponding public sequencing data from GEO and generate an appropriate gene-count matrix.

## Repository contents

```text
.
├── README.md
├── figures
└── GSE236155_RNAseq_analysis.Rmd
```

Generated result tables and figures may also be produced when running the R Markdown analysis.

## Author

**Sanny Bold**
MSc Bioinformatics
University of Edinburgh
