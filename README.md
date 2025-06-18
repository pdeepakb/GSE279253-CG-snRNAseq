# Single-Nucleus RNA-seq Analysis of Rat Celiac Ganglion (GSM8565269)

This repository reproduces the single-nucleus RNA-seq (snRNA-seq) analysis of the celiac ganglion dataset (`GSM8565269`) from [GSE279253](https://www.ncbi.nlm.nih.gov/geo/query/acc.cgi?acc=GSE279253), part of the article published in *Scientific Reports*:

> **The neuronal and glial cell diversity in the celiac ganglion revealed by single-nucleus RNA sequencing**  
> [Link to article](https://www.nature.com/articles/s41598-025-89779-3)

## 🧪 Analysis Steps

- Preprocessing and QC using Seurat
- Doublet removal with DoubletFinder
- PCA and clustering (resolution = 0.5)
- Marker gene detection with Wilcoxon test
- GO enrichment using clusterProfiler (alternative to GOrilla)
- Cell type annotation using `scType`

## 📂 Repository Structure

- `analysis/`: RMarkdown and plots
- `data/`: Raw data (not uploaded to GitHub)
- `results/`: Cluster markers and processed Seurat object
- `markers/`: Optional custom markers for annotation

## 🧬 Requirements

Install required R packages including `Seurat`, `DoubletFinder`, `clusterProfiler`, `org.Rn.eg.db`, `scType`.

## 📜 License

MIT License

---

**Author:** Deepak Poduval  
**Affiliation:** David Braun Lab, Yale University
