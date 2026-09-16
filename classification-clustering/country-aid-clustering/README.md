# Country Development Clustering for Humanitarian Aid Allocation

Unsupervised learning project that groups countries according to socioeconomic and health indicators in order to support humanitarian aid prioritization.

The project applies **feature engineering, standardization, K-Means clustering and cluster profiling** to a dataset containing 167 countries.

---

## 🎯 Project Overview

The scenario considers an international humanitarian NGO that has raised approximately **$10 million** and needs to allocate its resources strategically.

Instead of predicting a predefined target, the project uses unsupervised learning to discover groups of countries with similar development profiles.

The complete workflow includes:

- Exploratory Data Analysis (EDA)
- Distribution and outlier analysis
- Correlation analysis
- Composite feature engineering
- Feature standardization
- K-Means clustering
- Hyperparameter selection
- Internal cluster evaluation
- PCA-based visualization
- Cluster profiling
- Humanitarian priority ranking

---

## 📊 Dataset

The dataset contains **167 countries** and nine numerical indicators covering demographic, health, trade and economic conditions.

Main variables include:

- Child mortality
- Life expectancy
- Fertility rate
- Health expenditure
- Exports
- Imports
- Income
- Inflation
- GDP per capita

The country name is used only as an identifier.

---

## 🔎 Exploratory Data Analysis

The exploratory analysis reveals strong differences in scale and distribution across variables.

Economic variables such as income and GDP per capita are strongly right-skewed, while several indicators contain extreme observations. These values are not automatically treated as errors because extreme socioeconomic profiles may be meaningful in a humanitarian context.

Correlation analysis also reveals substantial redundancy among several development indicators.

---

## 🧩 Feature Engineering

To reduce dimensionality while preserving interpretability, the original variables are grouped into three composite dimensions:

### Health

Combines:

- Child mortality
- Life expectancy
- Fertility rate
- Health expenditure

Higher values represent more favorable overall health conditions.

### Trade

Combines:

- Exports
- Imports

### Finance

Combines:

- Income
- GDP per capita
- Inflation

The resulting indicators are standardized before clustering because K-Means relies on Euclidean distance.

---

## 🤖 K-Means Clustering

K-Means is selected because the final feature space contains three continuous standardized indicators and the objective is to obtain compact and interpretable groups.

The number of clusters is evaluated from **k = 2 to k = 8** using:

- Inertia / Elbow Method
- Silhouette Score
- Calinski-Harabasz Score
- Davies-Bouldin Score

The original analysis selects **k = 4** as the best practical compromise between clustering quality and interpretability.

---

## 📈 Model Evaluation

The final four-cluster model achieved:

| Metric | Result |
|---|---:|
| Silhouette Score | **0.3761** |
| Calinski-Harabasz Score | **111.06** |
| Davies-Bouldin Score | **0.8279** |

These values indicate a meaningful but not perfectly separated cluster structure, which is expected for socioeconomic country data where boundaries between development profiles are gradual rather than absolute.

PCA is used only for **2D and 3D visualization** and does not influence the cluster assignments.

---

## 🌍 Humanitarian Aid Prioritization

A key methodological point is that K-Means cluster identifiers are arbitrary. Cluster `0`, `1`, `2` or `3` does not inherently correspond to a specific level of humanitarian need.

The project therefore profiles each cluster using variables considered especially relevant to the NGO:

- **Income**
- **Child mortality**

A vulnerability score is then constructed so that:

- Lower income increases vulnerability.
- Higher child mortality increases vulnerability.

Clusters are ranked from **highest to lowest humanitarian priority** based on these observed socioeconomic profiles rather than on their numeric cluster labels.

A world choropleth map is used to visualize the resulting aid priorities geographically.

---

## 💡 Key Takeaways

- Distance-based clustering requires careful feature scaling.
- Socioeconomic data often contains meaningful skewness and extreme observations.
- Correlated variables can be condensed into interpretable composite indicators.
- K-Means provides a practical segmentation of countries into development profiles.
- Internal clustering metrics should be combined with domain interpretability when choosing the number of clusters.
- Cluster IDs are arbitrary and should never be directly interpreted as ordinal categories.
- Humanitarian priorities should be derived from cluster characteristics, not from the label assigned by the algorithm.
- Unsupervised learning is best treated as a **decision-support mechanism**, not as an automatic resource-allocation rule.

---

## ⚠️ Limitations and Potential Improvements

The analysis uses a static dataset and therefore does not capture changes in socioeconomic conditions over time.

Potential improvements include:

- Adding education, inequality, conflict and access-to-basic-services indicators
- Comparing K-Means with hierarchical or density-based clustering
- Testing cluster stability across different samples or time periods
- Comparing the resulting groups with external indicators such as the Human Development Index
- Incorporating expert humanitarian knowledge into final prioritization decisions

---

## 🛠️ Technologies

- **Python**
- **Pandas**
- **NumPy**
- **Scikit-learn**
- **Matplotlib**
- **Seaborn**
- **Plotly**
- **Jupyter Notebook / Google Colab**

Main techniques:

`EDA` · `Feature Engineering` · `StandardScaler` · `K-Means` · `Silhouette Score` · `Calinski-Harabasz` · `Davies-Bouldin` · `PCA` · `Cluster Profiling` · `Unsupervised Learning`

---

## 📁 Project Structure

```text
country-aid-clustering/
│
├── README.md
└── notebooks/
    └── country_aid_clustering.ipynb
```

The notebook contains the complete clustering workflow, including preprocessing, feature engineering, model selection, evaluation, visualization and humanitarian interpretation.

---

## 🎓 Context

This project was developed as part of the **Classification and Clustering** course within the **Master's Degree in Applied Artificial Intelligence**.

It has been reorganized and documented as part of this technical portfolio while preserving the original methodology and results.