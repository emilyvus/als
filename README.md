# CP-ALS:  A Cross-Population Framework for Amyotrophic Lateral Sclerosis Genomic Analysis and Modeling 

Contact: Emily Vu (emilyvu09@gmail.com)

Amyotrophic lateral sclerosis (ALS) is an incurable neurodegenerative disease. Although its genetic causes are complex, most genetic research on ALS has focused primarily on North American and European populations, underscoring the need for further investigation in other underrepresented populations. To address this gap, this study developed a novel cross-population genomic framework that integrates data from the 1000 Genomes Project and NCBI, encompassing 25 populations, over 3,000 genomes, and 34 genes.

This pipeline performs data preprocessing, variant profiling, population clustering, and predictive modeling. Population clusters were identified using variant mean profiles through t-distributed stochastic neighbor embedding (t-SNE). Inter- and intra-cluster analyses using statistical heatmaps, t-tests, and principal component analysis revealed distinct variant signatures across clusters, reflecting genetic similarity across regions of geographic proximity.

For each cluster, machine learning models were trained to predict variant counts of a target ALS gene using profiles of other genes, achieving robust performance (RMSE ≈ 1.0). These models accurately inferred variant distributions for underrepresented populations based on data from genetically similar groups within the same cluster. Recognizing the genetic overlap between ALS and frontotemporal dementia (FTD), the ALS-derived clusters were also used to develop predictive models for FTD, achieving comparable accuracy. 

This study is the first to construct population-based genomic profiles for ALS and to demonstrate transferable modeling across related neurodegenerative diseases. It establishes a scalable machine learning framework for studying genetic disorders in diverse populations with limited genetic data and supports the development of diagnostic strategies.

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

### Root Files

| File | Description |
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
