# CP-ALS Framework Pipeline

## Overview

This study presents CP-ALS, a cross-population genomic framework designed to analyze
genetic variation in Amyotrophic Lateral Sclerosis (ALS) across global populations.
The framework integrates multiple open-source datasets, identifies population
clusters based on genetic similarity, and builds machine learning models to
predict ALS and FTD gene variation.

---

## Step 1 — Data Collection

We collected open-source genomic datasets from several sources:

- hg38 variant data from the 1000 Genomes Project
- 25 global populations from NCBI
- Each population includes approximately 100–180 genomes
- Variant positions across 34 ALS-related genes from Coriel Institute

These datasets provide a diverse representation of global ALS-related genetic
variation.

### Populations (Region-Colored)

| Region     | Population Name                                 | Code | Samples | Country      |
|------------|--------------------------------------------------|------|---------|--------------|
| 🟩 Africa  | Esan in Nigeria                                 | ESN  | 173     | Nigeria      |
| 🟩 Africa  | Gambian in Western Division – Mandinka          | GWD  | 179     | Gambia       |
| 🟩 Africa  | Luhya in Webuye, Kenya                          | LWK  | 120     | Kenya        |
| 🟩 Africa  | Mende in Sierra Leone                           | MSL  | 128     | Sierra Leone |
| 🟩 Africa  | Yoruba in Ibadan, Nigeria                       | YRI  | 120     | Nigeria      |
| 🟦 Americas| African Ancestry in SW USA                      | ASW  | 62      | USA          |
| 🟦 Americas| African Caribbean in Barbados                   | ACB  | 120     | Barbados     |
| 🟦 Americas| Colombian in Medellín, Colombia                 | CLM  | 136     | Colombia     |
| 🟦 Americas| Mexican Ancestry in Los Angeles, USA            | MXL  | 71      | USA          |
| 🟦 Americas| Peruvian in Lima, Peru                          | PEL  | 122     | Peru         |
| 🟦 Americas| Puerto Rican in Puerto Rico                     | PUR  | 139     | Puerto Rico  |
| 🟧 East Asia| Chinese Dai in Xishuangbanna, China             | CDX  | 102     | China        |
| 🟧 East Asia| Han Chinese in Beijing, China                   | CHB  | 120     | China        |
| 🟧 East Asia| Han Chinese South                               | CHS  | 163     | China        |
| 🟧 East Asia| Japanese in Tokyo, Japan                        | JPT  | 120     | Japan        |
| 🟧 East Asia| Kinh in Ho Chi Minh City, Vietnam               | KHV  | 124     | Vietnam      |
| 🟪 Europe  | British From England and Scotland               | GBR  | 100     | UK           |
| 🟪 Europe  | Finnish in Finland                              | FIN  | 103     | Finland      |
| 🟪 Europe  | Iberian Populations in Spain                    | IBS  | 157     | Spain        |
| 🟪 Europe  | Toscani in Italia                               | TSI  | 114     | Italy        |
| 🟨 South Asia| Bengali in Bangladesh                           | BEB  | 144     | Bangladesh   |
| 🟨 South Asia| Gujarati Indians in Houston, USA                | GIH  | 109     | USA          |
| 🟨 South Asia| Indian Telugu in the U.K.                       | ITU  | 118     | UK           |
| 🟨 South Asia| Punjabi in Lahore, Pakistan                     | PJL  | 158     | Pakistan     |
| 🟨 South Asia| Sri Lankan Tamil in the UK                      | STU  | 128     | UK           |


**Reference**: https://www.coriell.org/1/NHGRI/Collections/1000-Genomes-Project-Collection/1000-Genomes-Project 


---

## Step 2 — Data Preprocessing

The collected datasets were cleaned, standardized, and merged into a unified
structure.

The final dataset forms a three-dimensional variant data cube:

Population × Genome × Gene

This cube represents variant counts for each gene across all genomes and
populations.

---

## Step 3 — Population Clustering

To identify genetically similar populations, we applied three clustering
algorithms:

- KMeans
- Gaussian Mixture Models
- Agglomerative Clustering

Clustering was performed with k = 3, 5, and 7 clusters.

The input to each clustering algorithm was a two-dimensional matrix:

- Rows represent 25 populations
- Columns represent 34 ALS genes
- Each cell contains the mean variant count per gene.

---

## Step 4 — Cluster Validation

Cluster quality was evaluated using both objective metrics and visualization
methods.

### Objective Validation

Cluster quality was measured using the Silhouette Coefficient, a standard
metric widely used in data mining.

The highest Silhouette score was obtained when k = 5, indicating optimal
cluster structure.

### Visualization Validation

We performed validation at three biological scales.

**Population Level:**

t-SNE was used to project the variant cube into a 25 × 2 matrix for
visualization.

**Genome Level:**

PCA was used to project genomes within populations into two-dimensional
space, allowing visualization of genome distributions across populations.

**Gene Level:**

t-tests were performed for three major ALS genes:

- SOD1
- FUS
- TARDBP

Gene-level comparisons showed significant differences between clusters.

### Validation Outcome

All validation analyses showed that populations within the same cluster share
strong genetic similarity, while populations in different clusters are clearly
separated.

Based on these results, k = 5 clusters were selected for downstream modeling.

---

## Step 5 — ALS Machine Learning Models

Within each cluster, machine learning models were developed to predict ALS
gene variant counts.

**Models used:**

- Linear Regression
- Random Forest Regressor
- Support Vector Regressor

**Training Strategy:**

Within each cluster, all populations except one were used as the training set.
The remaining population was used as the test set. This process was repeated
so each population served as a test population.

**Target Variables:**

- FUS
- SOD1
- TARDBP

**Features:**

Mean variant counts of the remaining ALS genes.

**Performance Metrics:**

- RMSE
- MAE

**Method Comparison:**

Performance of CP-ALS was compared against two baseline methods:

- Cluster-Pair: One cluster used for training and another for testing
- Leave-One-Cluster-Out (LOCO): All clusters except one used for training

Dot plots with 95% confidence intervals were used to visualize performance.

---

## Step 6 — ALS to FTD Transfer Learning

To evaluate cross-disease predictive power, transfer learning experiments
were performed using the population clusters.

Machine learning models were trained to predict variant counts of major
FTD genes:

- MAPT
- GRN
- CHMP2B

Features consisted of mean variant counts of genes shared between ALS and FTD.

**Training Strategy:**

Within each cluster, all populations except one were used for training and
the remaining population was used for testing.

**Performance Metrics:**

- RMSE
- MAE

Dot plots with 95% confidence intervals were used to evaluate model
performance.

---

## Conclusions

The CP-ALS framework demonstrates that clustering populations based on
genetic similarity improves prediction of ALS gene variation.

The framework also shows strong transferability between ALS and FTD,
suggesting shared genetic architecture across neurodegenerative diseases.
