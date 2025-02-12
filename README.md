AI Bootcamp Project 2

## 📌 Project Overview
Bird flu is currently spreading in the US, posing a significant **public health risk** due to its **zoonotic potential** and causing economic damage to the poultry industry. This project aims to **analyze the severity of different bird flu strains using genomic data**.

### **Key Research Questions:**
1. **Which strains of bird flu are the most dangerous?**
2. **How does bird flu compare to other flu outbreaks in the United States?**

### Why Machine Learning?
Machine learning helps us process large datasets efficiently while improving accuracy. We will apply:
- **K-Means Clustering** & **PCA (Principal Component Analysis)** for data exploration.
- **Classification models** (Random Forest, CNNs) for sequence classification.

## 📌 Data Collection & Sources
We have gathered data from multiple reputable sources, ensuring that our analysis is based on **official and scientifically validated data**. The process of data collection involved **extracting structured datasets from government and health organization portals, preprocessing them for inconsistencies, and integrating them into our analysis pipeline.**

### Primary Data Source:**
- Centers for Disease Control and Prevention (CDC)** - [Bird Flu Situation Summary](https://www.cdc.gov/bird-flu/situation-summary/index.html)
  - Data includes **geographical spread**, **infection rates**, and **clinical outcomes** of bird flu strains across different states.
  - We extracted reported cases of **H5N1 and other avian influenza strains** from CDC's public datasets.

### Secondary Data Sources:**
- Global Initiative on Sharing All Influenza Data (GISAID)** - [https://gisaid.org/](https://gisaid.org/)
  - Provides genomic sequencing data** of flu strains, essential for understanding viral mutations.
  - Data was retrieved through API requests and structured CSV formats.

- World Health Organization (WHO)** - [https://www.who.int/](https://www.who.int/)
  - Used for global perspective on bird flu trends** and **cross-country comparisons**.
  - WHO publications were parsed for trend reports and structured into time-series datasets.

- Data.gov (US Government Open Data Portal)** - [H5N1 Dataset Collection](https://catalog.data.gov/dataset/?q=H5N1+&sort=views_recent+desc&tags=avian-influenza&ext_location=&ext_bbox=&ext_prev_extent=)
  - Provided historical records of avian flu outbreaks, economic impacts on the poultry industry, and state-wise prevalence.
  - Data was cleaned using Python’s **Pandas library** to remove inconsistencies and missing values.

## 📌 Data Files in This Repository
We have uploaded several datasets and processing notebooks that document each step of our analysis:

| File Name | Description |
|-----------|-------------|
| **co-est2023-pop-updated.csv** | Population estimates used for regional flu prevalence analysis. Sourced from **Data.gov**. |
| **commercial-backyard-flocks.csv** | Data on flu outbreaks in **commercial vs backyard poultry flocks**, extracted from **CDC reports**. |
| **hpai-wild-birds.csv** | High Pathogenic Avian Influenza (HPAI) cases in **wild birds**, sourced from WHO's open-access dataset. |
| **mn_analysis_prj2.ipynb** | **Machine learning analysis & feature engineering**, processing structured influenza datasets. |
| **Data_Investigation.ipynb** | **Initial data exploration and cleaning** with visualization of infection trends. |
| **Data_Preprocessing_Round_2.ipynb** | **Advanced data preprocessing & transformation** including missing value imputation and normalization. |

## 📌 Project Team
**Team Name:** The Flockbusters 🦠🐦
- **Christopher Davis**
- **Matthew Ward**
- **Caleb Kelson**
- **Mary Pulley**
- **Madhavi Nithianandam**
- **Katie Craig**

**TA:** Revati
