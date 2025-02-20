AI Bootcamp Project 2

## 📌 Project Overview
Bird flu is currently spreading in the US, posing a significant **public health risk** due to its **zoonotic potential** and causing economic damage to the poultry industry. This project aims to **analyze the severity of different bird flu strains using genomic data**.

### **Key Research Questions:**
1. **Can we predict future outbreaks of Avian flu based on historic data using a times series model?**
2. **Can we group related outbreaks by their qualities across the United States?**

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
| **HPAI Detections in Mammals.csv** | H5N1 casses in Mammals
| **backyard_flock_old.csv** | Data on flu outbreaks in **commercial vs backyard poultry flocks**, extracted from **CDC reports**. |
| **hpai-wild-birds.csv** | High Pathogenic Avian Influenza (HPAI) cases in **wild birds**, sourced from WHO's open-access dataset. |
| **weather.csv** | Weather realted datasets. |
| **proj2_birdflu_analysis.ipynb** | The main project notebook. |
| **US Counties.csv** | US State and County dataset with Latitude and Longitude values |

## 📌 H5N1: PCA and Clustering analysis

The analysis uses Principal Component Analysis (PCA) and K-means clustering to identify patterns and clusters in the data.

1. **Feature Preparation**: The features used for clustering include temperature, temperature anomaly, precipitation, Palmer Z-Index, the number of wild bird outbreaks, livestock outbreaks, mammal outbreaks, the total number of birds affected, and the total flock size. These features are scaled using StandardScaler to ensure they are on a similar scale.

2. **Elbow Analysis**: An elbow analysis is performed to determine the optimal number of clusters. The inertia (within-cluster sum of squares) is plotted against the number of clusters (k), and the "elbow" in the plot is used to identify the appropriate number of clusters.

3. **PCA and K-means Clustering**: Based on the elbow analysis, the optimal number of clusters is determined to be 4. PCA is then applied to the scaled features to reduce the dimensionality, and K-means clustering is performed on the transformed data to identify the 4 clusters.

## **Principal Component Analysis (PCA) and Clustering Summary**  

## **PCA Overview**  

### **PCA1 (First Principal Component):**  
- Represents the largest source of variation in the data.  
- Strongly influenced by outbreak severity (`Birds Affected`, `Flock Size`).  
- States further to the right on the plot have larger outbreaks.  

### **PCA2 (Second Principal Component):**  
- Represents the second-largest source of variation.  
- Heavily influenced by temperature and precipitation.  
- States higher up on the plot tend to have higher temperatures and precipitation.  

---

## **Cluster Breakdown**  

### **Cluster 0: Southern/Southeastern States**  
- **States:** Alabama, Arkansas, Florida, Georgia, Kentucky, Louisiana, Mississippi, Missouri, North Carolina, Oklahoma, Oregon, Rhode Island, South Carolina, Tennessee, Texas, Virginia  
- **Characteristics:**  
  - Includes **Texas** and most southeastern states.  
  - **Moderate outbreak sizes:** ~935,000 birds affected.  
  - **Highest average temperatures and precipitation.**  
  - **Moderate number of wild bird outbreaks.**  

---

### **Cluster 1: Major Outbreak States**  
- **States:** California, Iowa, Ohio  
- **Characteristics:**  
  - Characterized by **massive outbreaks** (~24.8 million birds affected on average).  
  - **Highest number of both wild bird and livestock outbreaks.**  
  - **Moderate temperatures** with **varied precipitation.**  

---

### **Cluster 2: Northern States**  
- **States:** Colorado, Maine, Michigan, Minnesota, Montana, New Mexico, New York, North Dakota, South Dakota, Vermont, Washington, Wisconsin  
- **Characteristics:**  
  - Includes **northern states with colder climates.**  
  - **Moderate to large outbreaks:** ~3.2 million birds affected.  
  - **High number of wild bird outbreaks.**  
  - **Lowest average temperatures.**  

---

### **Cluster 3: Mixed/Moderate Impact States**  
- **States:** Arizona, Connecticut, Delaware, District of Columbia, Idaho, Illinois, Indiana, Kansas, Maryland, Massachusetts, Nebraska, Nevada, New Hampshire, New Jersey, Pennsylvania, Utah, West Virginia, Wyoming  
- **Characteristics:**  
  - A mix of **northeastern and central states.**  
  - **Smaller outbreak sizes:** ~1.6 million birds affected.  
  - **Lowest number of wild bird outbreaks.**  
  - **Moderate temperatures** and **lower precipitation.**

---  
## **Conclusions:**  
The identified clusters provide valuable insights into different patterns of HPAI transmission events:  
- **Wild Bird outbreaks** typically involve small flock sizes with few birds affected.  
- **Livestock outbreaks** involve larger flocks but show different levels of bird impact.  
- **Flock-based outbreaks** show the highest number of affected birds.  

## Analysis Results
    1. The elbow curve helps determine the optimal number of clusters (k=4)
    2. PCA reveals the main components of variation in the data
    3. The clustering shows distinct patterns in HPAI outbreaks across states
    4. Feature importance shows which variables contribute most to the patterns
    5. The top affected states by bird count are clearly identified

    
## 📌 H5N1 Outbreak Prediction (Binary classification model)
### Did an H5N1 outbreak occur at a specific location and time?


**Objective:**
Our objective was to develop a machine learning model to predict whether an H5N1 outbreak will occur based on spatial, temporal, and environmental factors.

---
**Datasets:**
1. Current Outbreak Data on Wild birds, Commercial Flock and Mammals
2. US county data with Latitudes and Longitudes
3. US Weather data based on State and County


**Target Variable:**
Outbreak Occurred (Binary: 1 = Outbreak, 0 = No Outbreak)

**Features:**
1.	***Spatial Features:***
*Latitude* (Geographic coordinate)
*Longitude* (Geographic coordinate)
2.	***Temporal Features:***
*Month* (Seasonal trends affecting virus spread)
*Year* (Long-term epidemiological patterns)
3.	***Environmental Factors:***
*Temperature* (Influences virus survival and transmission)
*Precipitation* (Potential impact on virus persistence in the environment)
4.	***Host-Related Features:***
*Bird Species* (Certain species are more susceptible)
*Mammal Species* (Tracking potential spillover events)
*Flock Type* (Backyard, commercial, wild populations)
*Flock Size* (Higher density may increase transmission risk)


### Features Correlation Heat map

![image](Data/hpai_heatmap.png)


### Key Observations from the Correlation Matrix:

#### Month and Outbreak Occurred (0.55 correlation):
A moderate positive correlation suggests that outbreaks may occur more frequently during specific months, potentially correlating with seasonal patterns (e.g., migratory periods).

#### HPAI Mammal Strain and Mammal Species (0.83 correlation):
HPAI Mammal Strain and Mammal Species have a high positive correlation (0.83), which suggests that that specific mammal species are more prone to certain HPAI strains.

#### Flock Type and Latitude (0.55 correlation):
Flock Type and Latitude have a moderate positive correlation, indicating that certain types of flocks might be located at specific latitudes.

#### HPAI Wildbird Strain and Latitude (0.43 correlation):
The HPAI Strain_x (Wild bird strain) has a moderate positive correlation with the Longitude which means certain bird species are specific to that longitudinal locations. 

### Month distribution of the Outbreak

![image](Data/hpao_month_distribution.png)

This data coincides with the 3 seasons in a sampling year

1. We see a pike in May, which is the breeding month.
2. Pike in November which coincides with fall migration.
3. December and January Months which are the wintering months

### Feature importance:

![image](Data/feature_importance.png)

**Month** is a major predictor of the outbreak data.

### Model Selection [Classification Model : Outbreak prediction]

Logistic Regression

### Model performance metrics

**Confusion Matrix**
The confusion matrix showed very few missed outbreaks 

**Classification Report**
The classification report showed a "Near perfect Model"

### Expected Outcomes:
1. A predictive model capable of estimating H5N1 outbreak risk in specific regions.
2. Insights into how environmental and host factors contribute to H5N1 outbreaks.
3. Potential applications in surveillance and early warning systems

---

## 📌 Forecasting Bird Flu Outbreak - ARIMA Time Series Model

The purpose of this code is to analyze the temporal patterns and characteristics of HPAI outbreaks using the provided datasets. The modeling approach focuses on time series analysis, including decomposition and feature engineering, to gain insights into the data. The key findings or conclusions of this analysis are not explicitly stated in the provided code, as it appears to be a part of a larger project or analysis.

1. **Imports and Data Loading**:
   - The code starts by importing various Python libraries for data manipulation, visualization, and time series analysis, such as Pandas, NumPy, Matplotlib, Seaborn, and statsmodels.
   - It then loads several CSV files containing data related to HPAI outbreaks, including flocks, livestock, mammals, wild birds, and weather data.

2. **Data Preprocessing**:
   - The code converts the 'Outbreak Date' column in each dataset to a datetime format.
   - It then aggregates the cases by date for each dataset (wild birds, mammals, livestock, and flocks) and sets the 'Outbreak Date' as the index.
   - The datasets are resampled to a daily frequency, and missing values are filled with zeros.

3. **Feature Engineering**:
   - The code creates additional features for the time series analysis, such as day of the week, quarter, month, year, day of the year, and rolling mean and standard deviation over a 7-day window.

4. **Time Series Decomposition**:
   - The code performs time series decomposition on the aggregated datasets using the seasonal_decompose function from statsmodels.
   - This allows the analysis of the trend, seasonality, and residual components of the time series.

5. **Visualization**:
   - The code includes several visualizations to explore the data, such as plotting the decomposed time series components for the wild birds, mammals, livestock, and flocks datasets.

**Notes about models**

- The notebook uses both manual ARIMA from statsmodels and auto_arima from pmdarima
- A custom evaluation function is created to fit ARIMA models with specified orders
- The implementation includes diagnostic tools like ACF (Autocorrelation Function) and PACF (Partial Autocorrelation Function) plots to determine appropriate model orders
- Handles seasonality through differencing
- Includes error metrics (MSE, MAE) for model evaluation
- Uses visualization tools to compare forecasts with actual data
- Implements proper time series cross-validation

The ARIMA implementation follows best practices for time series forecasting, with appropriate attention to model diagnostics and validation. The models are used both for understanding the temporal patterns in bird flu outbreaks and for making short-term forecasts. Overall, this code demonstrates a comprehensive approach to exploring and understanding the dynamics of HPAI outbreaks through time series analysis and visualization techniques.

## 📌 Project Team
**Team Name:** The Flockbusters 🦠🐦

Please see the branches for additional work, contributions and research

- **Christopher Davis**
- **Matthew Ward**
- **Caleb Kelson**
- **Mary Pulley**
- **Madhavi Nithianandam**
- **Katie Craig**

**TA:** Revati

## References
* https://www.cdc.gov/bird-flu/situation-summary/index.html
* https://gisaid.org/](https://gisaid.org/
* https://www.who.int/](https://www.who.int/
