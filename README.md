# 🏆 Bank churn dataset | Kaggle

> Predicting customer churn using bank customer data with additional macroeconomic features.

![Competition](https://img.shields.io/badge/Competition-Kaggle%20Playground%20S4E1-blue)
![Model](https://img.shields.io/badge/Model-LightGBM%20%2B%20Feature%20Engineering-green)
![Status](https://img.shields.io/badge/Status-Completed%20%2F%20Final%20Submission-yellow)

---

## 📌 Overview

This repository contains my solution for the **[Kaggle Playground Series S4E1](https://www.kaggle.com/competitions/playground-series-s4e1/)** competition.

The goal is to predict **customer churn** using structured customer-level features, enhanced with **external macroeconomic indicators** (e.g., CET1 capital ratios by country) to improve model generalizability and interpretability.

---

## 📂 Repository Structure



---

## 🔍 Problem Description

We are given anonymized customer data from a fictional bank. The objective is to predict whether a customer will **churn (leave the bank)** based on demographic, financial, and product usage data.

---

## 📈 Feature Engineering Highlights

- 🔢 **Macro-financial integration**:
  - Incorporated external **CET1 capital  (2016)** by country (France, Germany, Spain)
  - The CET1 ratio is an important indicator of a bank's financial soundness and is an external macro factor that can influence consumer confidence in banks and,churn behavior.
  - This Kaggle dataset is expected to be based on 2016 data. 
- 🧹 **Numerical processing**:
  - Winsorization & log transformation on skewed variables
  - Standardization for linear models
- 🧠 **Encoding**:
  - One-hot & ordinal encoding depending on model class
  - Target encoding tested but discarded due to overfitting risk


---

## 🧪 Modeling

| Model             | CV ROC AUC | Public LB | Notes |
|-------------------|------------|-----------|-------|
| XGBoost           | 0.859      | 0.861     | Baseline, fast tuning |
| LightGBM          | 0.860      | 0.860     | Slightly more stable |
| CatBoost   　　　  | 0.862      | 0.863     | Robust to missing/categorical |
| ⭐️Ensemble model⭐ | 0.829      | 0.827     | Linear baseline |

**Final submission:** CatBoost with full feature set + external CET1 + stratified 5-fold

---

## 📊 EDA Highlights

- Clear age-churn correlation (inverted U-shape)
- Geography plays significant role; CET1 adjustment helps smooth this effect
- Low balance customers churn more; tenure and activity history modulate this

---

## 🚀 How to Reproduce


1. Clone this repo:
   ```bash
   git clone https://github.com/yourusername/kaggle-s4e1-churn.git
   cd kaggle-s4e1-churn


2. Install dependencies:
  pip install -r requirements.txt


3. Run pipeline:

  python src/train.py --config=configs/default.yaml


🧠 Key Learnings
Incorporating external macroeconomic data like CET1 ratios adds predictive signal and encourages real-world thinking beyond the dataset.

Feature engineering remains king—especially when combined with simple models.

LightGBM and CatBoost continue to outperform on structured tabular tasks with minimal tuning.

📚 References
European Central Bank CET1 Reports

Seaborn Palette Cheatsheet

Kaggle Forum Discussions on S4E1
