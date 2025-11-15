# CP-ALS:  A Cross-Population Framework for Amyotrophic Lateral Sclerosis Genomic Analysis and Modeling 

Contact: Emily Vu (emilyvu09@gmail.com)

Amyotrophic lateral sclerosis (ALS) is an incurable neurodegenerative disease. Although its genetic causes are complex, most genetic research on ALS has focused primarily on North American and European populations, underscoring the need for further investigation in other underrepresented populations. To address this gap, this study developed a novel cross-population genomic framework that integrates data from the 1000 Genomes Project and NCBI, encompassing 25 populations, over 3,000 genomes, and 34 genes.

This pipeline performs data preprocessing, variant profiling, population clustering, and predictive modeling. Population clusters were identified using variant mean profiles through t-distributed stochastic neighbor embedding (t-SNE). Inter- and intra-cluster analyses using statistical heatmaps, t-tests, and principal component analysis revealed distinct variant signatures across clusters, reflecting genetic similarity across regions of geographic proximity.

For each cluster, machine learning models were trained to predict variant counts of a target ALS gene using profiles of other genes, achieving robust performance (RMSE ≈ 1.0). These models accurately inferred variant distributions for underrepresented populations based on data from genetically similar groups within the same cluster. Recognizing the genetic overlap between ALS and frontotemporal dementia (FTD), the ALS-derived clusters were also used to develop predictive models for FTD, achieving comparable accuracy. 

This study is the first to construct population-based genomic profiles for ALS and to demonstrate transferable modeling across related neurodegenerative diseases. It establishes a scalable machine learning framework for studying genetic disorders in diverse populations with limited genetic data and supports the development of diagnostic strategies.
