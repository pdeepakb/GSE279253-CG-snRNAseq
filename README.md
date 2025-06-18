# Single-Nucleus RNA-seq Analysis of Rat Celiac Ganglion (`GSM8565269`)

This repository reanalyses the single-nucleus RNA-seq (snRNA-seq) analysis of the **celiac ganglion dataset** (`GSM8565269`) from [**GSE279253**](https://www.ncbi.nlm.nih.gov/geo/query/acc.cgi?acc=GSE279253), as presented in the following *Scientific Reports* article:

> **The neuronal and glial cell diversity in the celiac ganglion revealed by single-nucleus RNA sequencing**
> [Read the article](https://www.nature.com/articles/s41598-025-89779-3)

---

## 🔬 Why Single-Cell/Nucleus RNA-seq?

* Enables the study of **cell types and states** in complex tissues via per-nucleus gene expression.
* Reveals **cellular heterogeneity** that bulk RNA-seq fails to detect.
* Key goals:

  * Cluster cells based on expression profiles
  * Identify marker genes
  * Annotate cell types

---

## 🧾 Summary: snRNA-seq Analysis of Rat Celiac Ganglion (GSM8565269)

This analysis focuses on a **single-nucleus RNA-seq dataset from the celiac ganglion** of a normal male Sprague-Dawley rat. The data were generated using 10x Genomics technology and analyzed with R.

### 🔧 Analysis Workflow

1. **Data Loading**

   * Read processed `.h5` file using `hdf5r`.
   * Manually constructed a sparse matrix (`dgCMatrix`) from raw counts.
   * Extracted metadata: barcodes, gene IDs, cell probabilities.

2. **Quality Control**

   * Filtered nuclei using mitochondrial gene percentage (`percent.mt`) and gene counts (`nFeature_RNA`).
   * Removed cells with >10% mitochondrial reads or <1,000 genes detected.

3. **Doublet Removal**

   * Used `DoubletFinder` after normalization and PCA.
   * Identified and removed likely doublets to retain high-confidence singlets.

4. **Dimensionality Reduction & Clustering**

   * Applied normalization, PCA (up to 40 components), and UMAP.
   * Constructed SNN graph and clustered cells at a resolution of 0.5.

5. **Marker Gene Analysis**

   * Identified differentially expressed genes with `FindAllMarkers` (Wilcoxon test).
   * Visualized top markers with violin plots and heatmaps.

6. **Neural Cell Type Annotation**

   * Annotated cells using `SingleR` with the `MouseRNAseqData` reference from `celldex`.
   * Integrated cell labels into the Seurat object; visualized with UMAP.

7. **Functional Enrichment**

   * Conducted GO Biological Process enrichment using `clusterProfiler`.
   * Highlighted neural differentiation and functional processes.

8. **Result Saving**

   * Saved the annotated Seurat object and marker results for reproducibility.

---

## 🛠️ Key Tools

| Tool                | Purpose                                  |
| ------------------- | ---------------------------------------- |
| **Seurat**          | Preprocessing, clustering, visualization |
| **DoubletFinder**   | Doublet detection and removal            |
| **SingleR**         | Cell type annotation                     |
| **celldex**         | Provides reference datasets for SingleR  |
| **clusterProfiler** | Gene ontology enrichment                 |

---

## 📁 Repository Structure

```
analysis/    # RMarkdown files and plots
data/        # Raw data files (not uploaded)
results/     # Cluster markers and processed Seurat object
```

---

## License

This project is licensed under the MIT License.

**Author:** Deepak Poduval
**Affiliation:** Braun Lab, Yale University
