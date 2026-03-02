# CP-ALS:  A Cross-Population Framework for Amyotrophic Lateral Sclerosis Genomic Analysis and Modeling 

Contact: Emily Vu (emilyvu09@gmail.com)

Amyotrophic lateral sclerosis (ALS) is a fatal neurodegenerative disease with complex genetic causes. Most ALS genetic studies have focused on European and North American populations, leaving many global populations underrepresented. To address this gap, this study developed CP-ALS, a novel cross-population genomic framework integrating variant data from the 1000 Genomes Project, NCBI, and ClinVar, encompassing 25 populations, over 3,000 genomes, and 34 ALS-associated genes. This framework constructs cluster-aware genomic variant profiles across diverse populations.

Population clusters were identified using mean variant profiles and rigorously validated using three clustering algorithms and the Silhouette Coefficient. Cluster stability was further verified through multi-level validation, including population-level visualization using t-SNE, genome-level analysis using principal component analysis (PCA), and gene-level statistical testing of major ALS genes (SOD1, FUS, TARDBP). These analyses consistently showed strong genetic similarity within clusters and clear separation between clusters.

Within each cluster, machine learning models were trained using leave-one-population-out validation to predict variant counts of target ALS genes. A total of 675 models were evaluated and consistently achieved lower RMSE and MAE than Cluster-Pair and Leave-One-Cluster-Out baselines, demonstrating the effectiveness of cluster-aware modeling for underrepresented populations.

Using the same population structure, transfer learning from ALS to frontotemporal dementia (FTD) achieved comparable prediction accuracy for major FTD genes. Models trained on ALS-derived clusters successfully predicted FTD variant counts, suggesting that shared genetic architecture between ALS and FTD can be leveraged for genomic prediction, particularly in populations with limited disease-specific data.

This study establishes the first scalable population-based genomic profiling framework for ALS and demonstrates transferable cluster-informed modeling across neurodegenerative diseases.

-----------------------------------------------------------------

## Publications & Presentations

- **CP-ALS: A Novel Cross-Population Framework for Amyotrophic Lateral Sclerosis Genomic Analysis & Modeling**, Emily Vu, Poster Presentation, *9th Annual HeLa: Ethics, Research and Access Conference and Research Symposium*,  New York Medical College, 02/2026

-----------------------------------------------------------------

## 📁 Project Structure

```
als/
├── README.md
├── INSTALL.md
├── CP-ALS.md
├── pyproject.toml
└── notebooks/
    ├── clustering_comparison_SC.ipynb
    ├── population_level_validation_tsne.ipynb
    ├── genome_level_validation_pca.ipynb
    ├── gene_level_validation_heatmap.ipynb
    └── als2als_prediction_SOD1.ipynb
```

### Files

| Name | Description |
|------|-------------|
| `README.md` | Project overview, abstract, and high-level summary of the CP-ALS framework. |
| `INSTALL.md` | Step-by-step installation and setup guide covering Conda environment creation, dependency installation, Jupyter kernel registration, and notebook launch instructions. |
| `CP-ALS.md` | Detailed description of the full CP-ALS pipeline, including data collection, preprocessing, population clustering, cluster validation, ALS machine learning models, and ALS-to-FTD transfer learning. |
| `pyproject.toml` | Python project configuration file defining the package metadata, required Python version (≥3.12), and all runtime dependencies (NumPy, pandas, scikit-learn, matplotlib, seaborn, JupyterLab, etc.). |

### `notebooks/`

| Notebook | Description |
|----------|-------------|
| `clustering_comparison_SC.ipynb` | Compares KMeans, Gaussian Mixture Models, and Agglomerative Clustering across different values of k (3, 5, 7) using the Silhouette Coefficient to identify the optimal number of population clusters. |
| `population_level_validation_tsne.ipynb` | Validates population clusters at the population level by projecting the variant mean profiles of 25 populations into 2D space using t-SNE, and visualizing cluster separation. |
| `genome_level_validation_pca.ipynb` | Validates clusters at the genome level by applying PCA to project individual genomes within each population into 2D space, confirming intra-cluster genetic similarity. |
| `gene_level_validation_heatmap.ipynb` | Validates clusters at the gene level using statistical heatmaps and t-tests on key ALS genes (SOD1, FUS, TARDBP) to reveal distinct variant signatures across clusters. |
| `als2als_prediction_SOD1.ipynb` | Trains and evaluates machine learning models (Linear Regression, Random Forest, SVR) to predict SOD1 variant counts using a cluster-based leave-one-out cross-validation strategy, and benchmarks against Cluster-Pair and LOCO baselines. |
