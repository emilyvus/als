# CP-ALS:  A Cross-Population Framework for Amyotrophic Lateral Sclerosis Genomic Analysis and Modeling 

Contact: Emily Vu (emilyvu09@gmail.com)

Amyotrophic lateral sclerosis (ALS) is an incurable neurodegenerative disease. Although its genetic causes are complex, most genetic research on ALS has focused primarily on North American and European populations, underscoring the need for further investigation in other underrepresented populations. To address this gap, this study developed a novel cross-population genomic framework that integrates data from the 1000 Genomes Project and NCBI, encompassing 25 populations, over 3,000 genomes, and 34 genes.

This pipeline performs data preprocessing, variant profiling, population clustering, and predictive modeling. Population clusters were identified using variant mean profiles through t-distributed stochastic neighbor embedding (t-SNE). Inter- and intra-cluster analyses using statistical heatmaps, t-tests, and principal component analysis revealed distinct variant signatures across clusters, reflecting genetic similarity across regions of geographic proximity.

For each cluster, machine learning models were trained to predict variant counts of a target ALS gene using profiles of other genes, achieving robust performance (RMSE ≈ 1.0). These models accurately inferred variant distributions for underrepresented populations based on data from genetically similar groups within the same cluster. Recognizing the genetic overlap between ALS and frontotemporal dementia (FTD), the ALS-derived clusters were also used to develop predictive models for FTD, achieving comparable accuracy. 

This study is the first to construct population-based genomic profiles for ALS and to demonstrate transferable modeling across related neurodegenerative diseases. It establishes a scalable machine learning framework for studying genetic disorders in diverse populations with limited genetic data and supports the development of diagnostic strategies.


# Populations (Sorted by Region)

| Region     | Population Name                                 | Code | Samples | Country      |
|------------|--------------------------------------------------|------|---------|--------------|
| Africa     | Esan in Nigeria                                 | ESN  | 173     | Nigeria      |
| Africa     | Gambian in Western Division – Mandinka          | GWD  | 179     | Gambia       |
| Africa     | Luhya in Webuye, Kenya                          | LWK  | 120     | Kenya        |
| Africa     | Mende in Sierra Leone                           | MSL  | 128     | Sierra Leone |
| Africa     | Yoruba in Ibadan, Nigeria                       | YRI  | 120     | Nigeria      |
| Americas   | African Ancestry in SW USA                      | ASW  | 62      | USA          |
| Americas   | African Caribbean in Barbados                   | ACB  | 120     | Barbados     |
| Americas   | Colombian in Medellín, Colombia                 | CLM  | 136     | Colombia     |
| Americas   | Mexican Ancestry in Los Angeles, USA            | MXL  | 71      | USA          |
| Americas   | Peruvian in Lima, Peru                          | PEL  | 122     | Peru         |
| Americas   | Puerto Rican in Puerto Rico                     | PUR  | 139     | Puerto Rico  |
| East Asia  | Chinese Dai in Xishuangbanna, China             | CDX  | 102     | China        |
| East Asia  | Han Chinese in Beijing, China                   | CHB  | 120     | China        |
| East Asia  | Han Chinese South                               | CHS  | 163     | China        |
| East Asia  | Japanese in Tokyo, Japan                        | JPT  | 120     | Japan        |
| East Asia  | Kinh in Ho Chi Minh City, Vietnam               | KHV  | 124     | Vietnam      |
| Europe     | British From England and Scotland               | GBR  | 100      | UK           |
| Europe     | Finnish in Finland                              | FIN  | 103      | Finland      |
| Europe     | Iberian Populations in Spain                    | IBS  | 157      | Spain        |
| Europe     | Toscani in Italia                               | TSI  | 114      | Italy        |
| South Asia | Bengali in Bangladesh                           | BEB  | 144      | Bangladesh   |
| South Asia | Gujarati Indians in Houston, USA                | GIH  | 109      | USA          |
| South Asia | Indian Telugu in the U.K.                       | ITU  | 118      | UK           |
| South Asia | Punjabi in Lahore, Pakistan                     | PJL  | 158      | Pakistan     |
| South Asia | Sri Lankan Tamil in the UK                      | STU  | 128      | UK           |

Reference: https://www.coriell.org/1/NHGRI/Collections/1000-Genomes-Project-Collection/1000-Genomes-Project 
