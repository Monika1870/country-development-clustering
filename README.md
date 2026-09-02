# Country Development Clustering

## Project Overview

This project uses **unsupervised machine learning** to group countries based on socio-economic and health-related indicators.

Three clustering techniques were applied and compared:

- **K-Means Clustering**
- **Hierarchical (Agglomerative) Clustering**
- **DBSCAN**

The main objective was to identify groups of countries with similar development characteristics and understand which clustering approach is most suitable for this dataset.

---

## Dataset

The dataset contains country-level socio-economic and health indicators.

### Features used

- `child_mort` – Child mortality rate
- `exports` – Exports as a percentage of GDP
- `health` – Health spending as a percentage of GDP
- `imports` – Imports as a percentage of GDP
- `income` – Average income
- `inflation` – Inflation rate
- `life_expec` – Life expectancy
- `total_fer` – Total fertility rate
- `gdpp` – GDP per capita

The `country` column was excluded from clustering because it is an identifier rather than a numerical feature.

---

## Project Workflow

### 1. Data Loading and Exploration
- Loaded the country development dataset using Pandas.
- Checked the dataset structure, data types and basic information.
- Explored the numerical variables using visualizations.

### 2. Data Preparation
- Removed the `country` identifier from the clustering features.
- Applied **StandardScaler** to standardize the numerical features before clustering.

### 3. K-Means Clustering
Different values of K were evaluated using the **Silhouette Score** and the **Elbow Method**.

Although K = 5 had a slightly higher Silhouette Score, it produced very small clusters. Therefore, **K = 3** was selected because it produced more balanced and interpretable clusters and was consistent with the Elbow Method.

K-Means results:

- WCSS (Inertia): **831.54**
- Silhouette Score: **0.286**
- Calinski-Harabasz Index: **66.22**

### K-Means Cluster Interpretation

The three clusters showed clear differences in socio-economic and health indicators:

- **Developed Countries** – higher income, GDP per capita and life expectancy, with lower child mortality.
- **Developing Countries** – moderate economic and health indicators.
- **Least Developed Countries** – lower income and GDP per capita, higher child mortality and fertility, and lower life expectancy.

---

## 4. Hierarchical Clustering

Hierarchical clustering was explored using a **dendrogram** with Ward linkage.

Different linkage methods were compared:

- Single
- Complete
- Average
- Ward

Ward linkage with **2 clusters** was selected for the final interpretation because it produced balanced and interpretable groups.

Results:

- Number of clusters: **2**
- Silhouette Score: **0.315**
- Calinski-Harabasz Index: **51.88**

The two groups broadly represented countries with lower and higher levels of socio-economic development.

---

## 5. DBSCAN

DBSCAN was also applied to identify dense groups and possible outlier countries.

Results:

- Clusters found: **2**
- Noise points: **46**
- Silhouette Score: **0.408**

DBSCAN identified countries that did not belong to dense groups as noise/outliers.

The DBSCAN Silhouette Score was calculated after excluding noise points, so it should **not be directly compared** with the K-Means and Hierarchical scores.

---

## Algorithm Comparison

| Algorithm | Clusters | Silhouette Score | Key Observation |
|---|---:|---:|---|
| K-Means | 3 | **0.286** | Three meaningful and balanced development groups |
| Hierarchical (Ward) | 2 | **0.315** | Two broad and interpretable development groups |
| DBSCAN | 2 + 46 noise | **0.408** | Identified outliers but classified many countries as noise |

---

## Final Conclusion

Three clustering algorithms were applied to group countries based on socio-economic and health indicators.

- **K-Means** produced three meaningful and well-balanced groups representing different levels of country development.
- **Hierarchical Clustering** produced two broad groups with clear development differences.
- **DBSCAN** successfully identified potential outlier countries, but many observations were classified as noise.
- Although DBSCAN had the highest Silhouette Score, its score was calculated after excluding noise points and therefore is not directly comparable with the other methods.
- **K-Means was selected as the most suitable approach for this dataset** because it grouped all countries into three meaningful and balanced development groups and made the results easier to interpret.

---

## Technologies Used

- Python
- Pandas
- NumPy
- Matplotlib
- Seaborn
- Scikit-learn
- SciPy
- Jupyter Notebook

---

## Repository Structure

```text
country-development-clustering/
│
├── country_development_clustering.ipynb
├── Country-data.csv
├── README.md
└── requirements.txt
```

---

## How to Run

1. Clone or download this repository.
2. Make sure `country_development_clustering.ipynb` and `Country-data.csv` are in the same folder.
3. Install the required libraries:

```bash
pip install -r requirements.txt
```

4. Open the notebook using Jupyter Notebook or JupyterLab.
5. Run the cells from top to bottom.

---

## Author

Monika Gautam

GitHub: https://github.com/Monika1870  
LinkedIn: https://www.linkedin.com/in/monika-gautam-7b09b0172/
