# Bulk RNA-seq DEG: KO vs WT (MorphiC Study 2 – GSE288289)

This repo contains a single Jupyter/R analysis notebook for bulk RNA-seq differential expression comparing **knockouts (KO)** vs **wild-type (WT)**, plus an optional **PDF report** with the write-up and figures.

- Notebook: `notebooks/Final.ipynb`
- PDF: `Final.pdf`

## Overview
- **Goal:** Analyze NIH **MorPhiC Bulk RNA-seq Study 2 (GSE288289)** to quantify transcriptome changes from **7 TF knockouts** in extra-embryonic lineages vs WT.
- **Comparisons:** (1) **All KO (n=19)** vs **All WT (n=15)** across seven TFs (34 samples total); (2) **MXD1 KO (n=3)** vs **MXD1 WT (n=3)**.

## Methods (two complementary approaches)
1) **edgeR (raw counts)**  
   `DGEList → filterByExpr → TMM → estimateDisp → exactTest`, saving DEGs to CSV and visualizing with MDS/MA, heatmaps, and volcano plots.
2) **Per-gene t-tests (TPM)**  
   Use pre-normalized **TPM**, filter **mean TPM > 1**, compute log2FC and **BH/FDR**, save CSV, and visualize with heatmaps and EnhancedVolcano.

## Visualizations
- **Heatmaps** (pheatmap/ComplexHeatmap), **Volcano** (ggplot2 / EnhancedVolcano), **MDS**/MA plots, and **Venn** overlaps of top-20 DEGs between methods.
  
## Data
- **Counts:** `GSE288289_study2_genesCounts.csv` (≈38,592 genes, 82 samples) with series metadata (GSE288289_series_matrix).
- **TPM:** `GSE288289_study2_genesTPM.csv.gz`, used for the t-test branch.

## Results
- **All KO vs WT:** edgeR with FDR control identifies significant DEGs; clustering and volcano plots show clear KO-vs-WT separation.
- **MXD1 KO vs WT:** both approaches detect expression shifts; TPM t-tests apply BH/FDR and log2FC, complementing edgeR’s dispersion model.
