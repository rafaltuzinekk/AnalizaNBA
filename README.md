# NBA Shot Analysis & Predictive Modeling 🏀

This repository contains an end-to-end data analytics and machine learning pipeline focused on NBA shot logs from the 2014-2015 season. The project aims to uncover patterns in player shooting behaviors and predict shot outcomes using spatial and temporal variables.

Originally conceptualized as an academic project in MATLAB, the entire analytical logic has been migrated, optimized, and rewritten in pure Python, utilizing industry-standard Data Science libraries.

## 🛠️ Tech Stack
* **Language:** Python 3.9+
* **Data Manipulation:** `pandas`
* **Machine Learning:** `scikit-learn`
* **Data Visualization:** `matplotlib`, `seaborn`

## 📊 Pipeline Overview

The analysis is divided into three core stages:

### 1. Data Preprocessing & Feature Engineering
Raw data is rarely ready for algorithms. The pipeline ensures data integrity through:
* **Feature Creation:** Calculating a custom `defender_pressure` index (ratio of defender distance to shot distance) and converting imperial units (feet) to the metric system (meters).
* **Missing Value Imputation:** Handling null values in the shot clock using statistical medians.
* **Outlier Handling:** Removing anomalous touch times utilizing the Interquartile Range (IQR) method and clipping extreme shot distances at the 99th percentile to ensure robust model training.

### 2. Exploratory Data Analysis (EDA)
A comprehensive statistical dashboard was generated to visually interpret the dataset:
* Distribution of throw distances.
* Time spent with the ball vs. overall shooting accuracy.
* Scatter plot mapping shot distance against the closest defender's distance.
* Individual player profiling (e.g., Stephen Curry), computing specific metrics such as average distance, variance, and success rate.

<img width="1784" height="982" alt="Diagrams" src="https://github.com/user-attachments/assets/79813732-6066-41c3-83a8-a1e6fde6f26e" />

### 3. Machine Learning Application
The project implements both unsupervised and supervised machine learning techniques:

* **Unsupervised Learning (K-Means Clustering):** Shots were segmented into three distinct `action_types` based on standardized touch time and shot distance. The algorithm successfully identified logical clusters: quick close-range shots, quick catch-and-shoot perimeter shots, and isolation plays with extended ball-handling time.

<img width="846" height="552" alt="Cluster" src="https://github.com/user-attachments/assets/20684190-b654-427c-aef0-bf022e1f7e20" />

* **Supervised Learning (Decision Tree Classifier):** A predictive model was trained to classify shot outcomes (`made` vs. `missed`). To prevent overfitting and optimize computational efficiency, **Principal Component Analysis (PCA)** was applied, retaining components that explain 95% of the data's variance. 

<img width="665" height="550" alt="matrix" src="https://github.com/user-attachments/assets/8d378a35-ee26-4f3d-a81c-a66140a9d752" />

## 💡 Key Findings
* The predictive model achieved a baseline accuracy of **~54%** on the test set. While seemingly modest, this highlights the inherent stochasticity and chaotic nature of basketball; predicting whether a shot goes in based strictly on basic spatial metrics is a highly complex task.
* The K-Means algorithm effectively mapped the modern NBA playstyle without being explicitly programmed with basketball rules.

## 🚀 How to Run
1. Clone this repository to your local machine.
2. Ensure you have the required libraries installed (`pip install pandas scikit-learn matplotlib seaborn`).
3. Run the `nba_analysis.ipynb` notebook in Visual Studio Code or Jupyter.
