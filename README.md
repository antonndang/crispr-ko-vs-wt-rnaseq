# Bulk RNA-seq DEG: KO vs WT (MorphiC Study 2 – GSE288289)

This repo contains a single Jupyter/R analysis notebook for bulk RNA-seq differential expression comparing **knockouts (KO)** vs **wild-type (WT)**, plus an optional **PDF report** with the write-up and figures.

- Notebook: `notebooks/Final3.ipynb`

## Overview
- **Goal:** Analyze NIH **MorPhiC Bulk RNA-seq Study 2 (GSE288289)** to quantify transcriptome changes from **7 TF knockouts** in extra-embryonic lineages vs WT. :contentReference[oaicite:0]{index=0} :contentReference[oaicite:1]{index=1}  
- **Comparisons:** (1) **All KO (n=19)** vs **All WT (n=15)** across seven TFs (34 samples total); (2) **MXD1 KO (n=3)** vs **MXD1 WT (n=3)**. :contentReference[oaicite:2]{index=2} :contentReference[oaicite:3]{index=3}

## Methods (two complementary approaches)
1) **edgeR (raw counts)**  
   `DGEList → filterByExpr → TMM → estimateDisp → exactTest`, saving DEGs to CSV and visualizing with MDS/MA, heatmaps, and volcano plots. :contentReference[oaicite:4]{index=4} :contentReference[oaicite:5]{index=5}  
2) **Per-gene t-tests (TPM)**  
   Use pre-normalized **TPM**, filter **mean TPM > 1**, compute log2FC and **BH/FDR**, save CSV, and visualize with heatmaps and EnhancedVolcano. :contentReference[oaicite:6]{index=6}

> The notebook shows how KO/WT groups and sample counts were created for **Goal 1 (34 samples)** and **Goal 2 (6 samples)**, and writes result CSVs. :contentReference[oaicite:7]{index=7} :contentReference[oaicite:8]{index=8} :contentReference[oaicite:9]{index=9} :contentReference[oaicite:10]{index=10}

## Visualizations
- **Heatmaps** (pheatmap/ComplexHeatmap), **Volcano** (ggplot2 / EnhancedVolcano), **MDS**/MA plots, and **Venn** overlaps of top-20 DEGs between methods. :contentReference[oaicite:11]{index=11} :contentReference[oaicite:12]{index=12} :contentReference[oaicite:13]{index=13}  
- Examples for both **All KO vs WT** and **MXD1 KO vs WT** are generated directly in the notebook. :contentReference[oaicite:14]{index=14} :contentReference[oaicite:15]{index=15}

## Data
- **Counts:** `GSE288289_study2_genesCounts.csv` (≈38,592 genes, 82 samples) with series metadata (GSE288289_series_matrix). :contentReference[oaicite:16]{index=16}  
- **TPM:** `GSE288289_study2_genesTPM.csv.gz`, used for the t-test branch. :contentReference[oaicite:17]{index=17}

## Results
- **All KO vs WT:** edgeR with FDR control identifies significant DEGs; clustering and volcano plots show clear KO-vs-WT separation. :contentReference[oaicite:19]{index=19}  
- **MXD1 KO vs WT:** both approaches detect expression shifts; TPM t-tests apply BH/FDR and log2FC, complementing edgeR’s dispersion model. :contentReference[oaicite:20]{index=20} :contentReference[oaicite:21]{index=21}
