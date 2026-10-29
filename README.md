# Country Schools: Preprocessing, Anomaly Detection & Clustering

## 📌 Project Overview
This repository contains Lab 2 for the Data Preprocessing course. The project focuses on performing essential data preprocessing, identifying anomalous counties, and applying unsupervised machine learning (clustering) to the Kenyan Country Schools dataset.

## 📊 Dataset
*   **File:** `Country Schools.csv`
*   **Description:** Data on school electrification and solar-kit delivery (LDDs/TDDs) across various counties in Kenya. 

## ⚙️ Key Methodology
1.  **Data Cleaning:** Removed blank rows and isolated the aggregate `TOTAL` row to prevent double-counting. Fixed mislabeled columns (`SNO` -> `County`) and converted string percentages into floats.
2.  **Feature Engineering:** Created new metrics such as `PendingRatio`, `LDDsPerInstalled`, and `log_TotalSchools`.
3.  **Anomaly Detection:** Used Z-scores, IQR, Isolation Forest, and Local Outlier Factor (LOF) to find unusual counties.
4.  **Cluster Analysis:** Scaled features and applied K-Means clustering (validated with the Elbow method and Silhouette scores) to segment the counties.

## 💡 Key Findings
*   **Redundancy:** `InstalledTDDs` is perfectly correlated to installed schools (exactly 2 per school), meaning it provides no extra information for clustering.
*   **Anomalies:** Arid and frontier counties (Mandera, Wajir, Marsabit, Turkana) are extreme anomalies. They have low installation rates despite having received high numbers of LDD kits (supply without installation).
*   **Clusters:** The K-Means algorithm (k=4) grouped the counties into four actionable segments:
    *   *Frontier-Low:* Low coverage, supply bottlenecks.
    *   *Large-Mid:* Huge absolute numbers, but average coverage.
    *   *Mid-High:* Benchmark counties with >90% coverage.
    *   *Small-High:* Small counties with excellent, cost-effective coverage.

## 🛠️ Tools Used
*   Python 3 (Pandas, NumPy)
*   Scikit-Learn (Isolation Forest, LOF, K-Means, PCA)
*   Matplotlib & Seaborn (Data Visualization)
*   Jupyter Lab

## 🚀 How to Run
1. Clone the repository:
   ```bash
   git clone https://github.com/Rukundo-elie/country-schools-lab.git