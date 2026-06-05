# A Multi-Age, Multi-Cause Analytics Framework for Childhood Mortality

## Project Overview

This project analyses global childhood mortality patterns using the WHO CA-CODE 2024 dataset across three age groups: **1–59 months**, **5–9 years**, and **10–14 years**. The aim of the project is to understand how causes of death change across childhood development stages and how countries can be grouped based on similar mortality structures.

The project combines **exploratory data analysis**, **feature engineering**, **unsupervised learning**, and **supervised machine learning** to identify age-specific mortality patterns, discover country-level mortality clusters, and predict the dominant cause of death from cause-share distributions.

The analysis shows a clear epidemiological transition: younger children are mainly affected by infectious diseases, while older children increasingly face risks from injuries and non-communicable diseases.

---

## Objectives

The main objectives of this project are:

* To analyse global childhood mortality across multiple age groups.
* To identify the leading causes of death for each childhood age category.
* To compare broad mortality groups such as infectious diseases, non-communicable diseases, injuries, and other causes.
* To engineer cause-share features for country-age mortality profiles.
* To apply K-Means clustering to group countries with similar mortality patterns.
* To use supervised machine learning models to predict the dominant cause of death.
* To interpret the results in a public-health and policy-planning context.

---

## Dataset

The project uses the **WHO CA-CODE 2024** cause-of-death dataset.

Three age-specific datasets were used:

* `CA-CODE-2024-1to59m.csv`
* `CA-CODE-2024-5to9.csv`
* `CA-CODE-2024-10to14.csv`

These datasets contain harmonised cause-of-death estimates by country, age group, year, indicator, and cause of death.

For methodological consistency, the analysis focuses on the **year 2000** because it provides complete global coverage and supports fair comparison across countries and age groups.

---

## Project Structure

```text
childhood-mortality-analysis/
│
├── data/
│   ├── CA-CODE-2024-1to59m.csv
│   ├── CA-CODE-2024-5to9.csv
│   └── CA-CODE-2024-10to14.csv
│
├── CA.ipynb
├── child_mortality_report.pdf
└── README.md
```

---

## Tools and Technologies

The project was developed using:

* Python
* Jupyter Notebook
* Pandas
* NumPy
* Matplotlib
* Seaborn
* Scikit-learn

Machine learning techniques used:

* K-Means Clustering
* Principal Component Analysis
* Logistic Regression
* Random Forest Classifier

---

## Methodology

### 1. Data Loading and Cleaning

The three WHO CA-CODE datasets were loaded into Python and merged into a single analytical dataset. Unnecessary fields were removed, missing values were handled, and the data was filtered to include only the `Deaths` indicator for the year 2000.

Key preparation steps included:

* Loading age-specific datasets
* Removing irrelevant columns
* Checking missing values and duplicates
* Merging datasets into one unified dataframe
* Standardising column names
* Filtering the dataset to the baseline year

---

### 2. Exploratory Data Analysis

Exploratory Data Analysis was conducted to understand global mortality trends across age groups.

The EDA included:

* Total deaths by age group
* Top 10 causes of death for each age group
* Broad cause-group comparison
* Country-level mortality heatmaps
* Cause correlation analysis

The analysis showed that infectious diseases dominate mortality in children aged 1–59 months, while injuries and non-communicable diseases become more prominent in older age groups.

---

### 3. Feature Engineering

The dataset was transformed into a machine-learning-ready format by calculating cause-share features.

Each row represents a unique **country-age profile**, and each feature represents the proportion of deaths caused by a specific cause.

Feature engineering steps included:

* Aggregating deaths by country, age group, and cause
* Calculating total deaths per country-age group
* Computing cause-share values
* Pivoting the data into wide format
* Creating features suitable for clustering and classification

This transformation allowed the project to compare countries based on mortality structure rather than raw death counts alone.

---

### 4. Clustering Analysis

K-Means clustering was applied to identify hidden mortality structures across countries and age groups. The Elbow Method was used to support the selection of the optimal number of clusters.

Principal Component Analysis was then used to visualise the clusters in two dimensions.

The clustering analysis identified four broad mortality profiles:

1. Countries with high communicable disease burden
2. Countries with injury and non-communicable disease patterns
3. Transitional countries with mixed mortality burdens
4. Countries with unusual or high-variability mortality structures

These clusters provide useful insights for health policy, intervention targeting, and resource allocation.

---

### 5. Supervised Machine Learning

Two supervised learning models were developed to predict the dominant cause of death for each country-age profile:

* Logistic Regression
* Random Forest Classifier

The dominant cause of death was created as the target label by selecting the cause with the highest share for each country-age profile.

The dataset was split into training and testing sets using stratified sampling to preserve class distribution.

---

## Model Performance

### Logistic Regression

Logistic Regression was used as the baseline model. It achieved moderate performance but struggled with minority classes and non-linear mortality patterns.

The model was useful for establishing a simple interpretable benchmark, but it was limited because childhood mortality patterns are complex, imbalanced, and often non-linear.

### Random Forest Classifier

The Random Forest model performed better than Logistic Regression. It achieved stronger classification results and handled non-linear cause-share relationships more effectively.

The model also provided feature importance outputs, helping to identify which mortality causes contributed most strongly to prediction.

Overall, the Random Forest model was more suitable for this project because it captured complex interactions between causes of death and produced more reliable predictions.

---

## Key Findings

The project produced several important findings:

* Children aged **1–59 months** are mainly affected by communicable diseases such as lower respiratory infections, diarrhoea, malaria, measles, and meningitis.
* Children aged **5–9 years** show a transitional mortality pattern, with infectious diseases still present but injuries and non-communicable diseases becoming more visible.
* Children aged **10–14 years** show a stronger shift toward injuries, road traffic incidents, drowning, cancers, congenital conditions, and other non-communicable diseases.
* K-Means clustering identified countries with similar mortality structures, showing that childhood mortality patterns are not random but structured.
* Random Forest achieved stronger predictive performance than Logistic Regression, suggesting that non-linear machine learning models are better suited for this type of mortality classification task.
* The findings support age-specific health intervention planning rather than treating childhood mortality as one uniform category.

---

## Visualisations

The notebook includes several visualisations, including:

* Bar charts of top causes of death by age group
* Broad cause-group comparison charts
* Country-level mortality heatmaps
* PCA visualisation of K-Means clusters
* Confusion matrix for Random Forest classification
* Feature importance plot
* Cluster count visualisation

These visualisations help communicate both the epidemiological patterns and machine learning results clearly.

---

## Business and Policy Value

Although this is a public-health project, the analytical approach has strong business analytics relevance. The results can support evidence-based decision-making for:

* Health ministries
* International health organisations
* NGOs
* Development agencies
* Public-health researchers
* Policy planners

The framework can help decision-makers identify high-risk age groups, prioritise interventions, compare country-level mortality structures, and allocate health resources more effectively.

---

## Ethical Considerations

This project uses aggregated country-level mortality data and does not involve individual-level personal data. However, ethical considerations remain important because mortality patterns can be affected by data quality, reporting differences, health inequality, poverty, conflict, and structural disadvantage.

The project avoids interpreting country-level patterns as cultural or national weaknesses. Instead, results are interpreted in relation to broader systemic factors such as healthcare access, environmental risk, socioeconomic inequality, and public-health infrastructure.

Machine learning results are treated as decision-support outputs rather than definitive predictions.

---

## Limitations

The project has several limitations:

* The analysis focuses only on the year 2000.
* Some countries may have lower-quality mortality reporting systems.
* Cause-of-death estimates may be affected by modelling assumptions.
* Minority mortality classes are harder to predict accurately.
* Socioeconomic, healthcare, and environmental variables were not included in the current model.

Future work could extend the project by adding multiple years, socioeconomic indicators, regional analysis, time-series modelling, and sub-national mortality data.

---

## Future Improvements

Potential future extensions include:

* Expanding the analysis across multiple years
* Adding income group, region, and health expenditure variables
* Applying advanced clustering techniques
* Testing additional classification models such as XGBoost or SVM
* Building an interactive dashboard using Streamlit, Power BI, or Tableau
* Adding geospatial visualisations
* Conducting trend analysis across time

---

## How to Run the Project

### 1. Clone the Repository

```bash
git clone https://github.com/your-username/childhood-mortality-analysis.git
cd childhood-mortality-analysis
```

### 2. Install Required Libraries

```bash
pip install pandas numpy matplotlib seaborn scikit-learn jupyter
```

### 3. Open the Notebook

```bash
jupyter notebook CA.ipynb
```

### 4. Run All Cells

Run the notebook from top to bottom to reproduce the data cleaning, EDA, clustering, modelling, and visualisation results.

---

## Repository Contents

| File                         | Description                                                                                            |
| ---------------------------- | ------------------------------------------------------------------------------------------------------ |
| `CA.ipynb`                   | Main Jupyter Notebook containing data cleaning, EDA, clustering, modelling, and visualisations         |
| `child_mortality_report.pdf` | Final project report explaining the background, methodology, findings, ethical issues, and conclusions |
| `data/`                      | Folder containing the WHO CA-CODE 2024 datasets                                                        |

---

## Conclusion

This project demonstrates how data mining and machine learning can be used to analyse global childhood mortality patterns across multiple age groups. The findings show that childhood mortality changes significantly with age, moving from infectious disease dominance in younger children toward injury and non-communicable disease burdens in older children.

By combining exploratory analysis, clustering, and supervised learning, the project provides a structured analytical framework that can support public-health planning, policy decisions, and targeted intervention design.

---

## Author

**Kyaw May Pyone Shinn**
MSc in Data Analytics
National College of Ireland
