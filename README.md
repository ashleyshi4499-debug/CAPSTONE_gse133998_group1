# Breast Cancer RNA-seq Capstone Project

## Overview

This project analyzes public RNA-seq data from GEO dataset GSE133998 to investigate transcriptomic differences between breast cancer tissues and matched adjacent normal tissues.

The analysis includes exploratory data analysis, differential gene expression analysis, pathway enrichment analysis, and transcriptomic drug repurposing.

## Research Question

What transcriptomic changes distinguish breast cancer tissues from matched adjacent normal tissues, and what biological pathways and candidate therapeutic compounds are associated with these changes?

## Dataset

- GEO accession: GSE133998
- Samples analyzed: 12 tissue samples
- Cancer tissues: 6
- Adjacent normal tissues: 6
- Study design: paired cancer and adjacent normal samples from six patients

Blood samples contained in the original dataset were excluded from this analysis.

## Analysis Workflow

1. Raw RNA-seq count data import
2. Sample metadata construction
3. Low-count gene filtering
4. Variance stabilizing transformation
5. Exploratory data analysis
   - PCA
   - Sample correlation heatmap
6. Differential expression analysis using DESeq2
7. DEG visualization
   - Volcano plot
   - Top DEG heatmap
8. Pathway enrichment analysis
   - Enrichr / ORA
   - FGSEA
9. Drug repurposing using LINCS gene-signature overlap

## Differential Expression

Differential expression was performed using a paired DESeq2 model:

`~ patient + condition`

Genes were classified as significantly differentially expressed using:

- adjusted p-value < 0.001
- |log2 fold change| > 1

A total of 738 significant DEGs were identified:

- 295 upregulated genes
- 443 downregulated genes

## Pathway Analysis

ORA and FGSEA identified major biological themes including:

- Interferon responses
- Immune and inflammatory signaling
- Cell-cycle regulation
- DNA replication
- E2F targets
- G2/M checkpoint activity

## Drug Repurposing

A disease signature was constructed using:

- Top 150 cancer-upregulated genes
- Top 150 cancer-downregulated genes

Of the 300 query genes, 152 were represented in the LINCS reference gene universe.

Drug signatures were ranked according to reverse gene-expression overlap.

Metformin was the highest-ranked compound–cell signature in the overlap analysis.

## Repository Structure

```text
data/
    processed/

figures/

results/
    differential_expression/
    enrichment/
    drug_repurposing/

scripts/

GSE133998_capstone.Rmd
README.md