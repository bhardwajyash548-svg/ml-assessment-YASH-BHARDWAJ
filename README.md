# ml-assessment-YASH-BHARDWAJ

# 📊 Machine Learning Fundamentals Assessment

This repository contains solutions for the **Machine Learning Fundamentals — Graded Assessment**, covering supervised learning, unsupervised learning, feature engineering, and business case analysis.

---

## 📁 Repository Structure

```
ml-assessment-yash/
│
├── part_a/
│   ├── q1_supervised.ipynb
│   ├── q2_unsupervised.ipynb
│   └── q3_feature_engineering.ipynb
│
├── part_b/
│   └── business_analysis.md
│
└── data/
    ├── q1_heart_disease.csv
    ├── q2_customers.csv
    └── q3_retail_promotions.csv
```

---

## 📌 Part A: Python Coding

### 🔹 Q1: Supervised Learning (Classification)

* Built multiple classification models:

  * Decision Tree
  * Random Forest
  * Gradient Boosting
* Performed:

  * Data preprocessing
  * Feature encoding & scaling
  * Model evaluation using Precision, Recall, F1-score
  * Hyperparameter tuning using GridSearchCV

---

### 🔹 Q2: Unsupervised Learning (Clustering)

* Applied **K-Means clustering** for customer segmentation
* Used **Elbow Method** to determine optimal clusters
* Performed:

  * PCA for dimensionality reduction
  * Cluster visualization
  * Business interpretation of customer segments

---

### 🔹 Q3: Feature Engineering & Regression

* Created new features from date column:

  * Year, Month, Day of Week, Month-End flag
* Built a **scikit-learn Pipeline** using:

  * ColumnTransformer
  * OneHotEncoder & StandardScaler
* Trained models:

  * Linear Regression
  * Random Forest Regressor
* Evaluated using:

  * RMSE & MAE
* Generated parity plots and feature importance analysis

---

## 📌 Part B: Business Case Analysis

Analyzed a real-world retail problem involving **promotion effectiveness across multiple stores**.

Key areas covered:

* Problem formulation (Regression setup)
* Data strategy and EDA planning
* Handling imbalance in promotions
* Model evaluation and deployment strategy
* Business-driven insights for decision making

---

## 📂 Datasets

All datasets are stored inside the `data/` folder and loaded using **relative paths**.

| File Name                  | Description                            |
| -------------------------- | -------------------------------------- |
| `q1_heart_disease.csv`     | Patient health data for classification |
| `q2_customers.csv`         | Customer behavior data for clustering  |
| `q3_retail_promotions.csv` | Retail transaction data for regression |

---

## ⚙️ Technologies Used

* Python 🐍
* Pandas & NumPy
* Scikit-learn
* Matplotlib & Seaborn
* Jupyter Notebook

---

## 🚀 How to Run

1. Clone the repository:

```
git clone <your-repo-link>
```

2. Navigate to project folder:

```
cd ml-assessment-yash
```

3. Open Jupyter Notebook:

```
jupyter notebook
```

4. Run notebooks inside `part_a/`

---

## ✅ Key Highlights

* End-to-end ML pipeline implementation
* Real-world business problem solving
* Strong focus on data preprocessing and feature engineering
* Model evaluation with proper metrics
* Clean and structured code

---

## 📌 Submission Notes

* All notebooks are pre-executed
* Repository is public
* Only this GitHub link is submitted as per guidelines

---

## 👤 Author

**Yash Bhardwaj**
Aspiring Business Analyst | Generative AI & Machine Learning Enthusiast

---
