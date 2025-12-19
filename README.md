# DS 301 Final Project – Bank Marketing and Customer Churn Classification

**Student:** Moataz Samara  
**Course:** DS 301 – Machine Learning Techniques  
**Instructor:** Mirza Zaeem Baig  

This repository contains my DS 301 final project.  
The project reproduces a real research paper on **Bank Marketing** and then **extends** the same methodology to a **Customer Churn** dataset.

---

## 1. Project Overview

The original research paper, *“A Data Driven Approach to Predict the Success of Bank Telemarketing”*, uses the **UCI Bank Marketing** dataset to predict whether a client will subscribe to a **term deposit** after a telemarketing call.

In this project I:

1. **Reproduce** the paper’s main approach using:
   - Logistic Regression  
   - Decision Tree  
2. **Extend** the work by:
   - Adding **SMOTE** to handle class imbalance  
   - Trying additional models (Random Forest, SVM, etc.)  
   - Applying the same pipeline to a second dataset: **Bank Customer Churn**

The main evaluation metric throughout the project is **ROC-AUC**, which is well-suited for imbalanced binary classification problems.

---

## 2. Datasets

### 2.1 Bank Marketing (UCI)

- **Source:** UCI Machine Learning Repository  
- **Task:** Predict if a client subscribes to a **term deposit** (`y` = yes / no).  
- **Type:** Binary classification  
- **Notes:**
  - Contains client demographics and campaign-related features
  - Target is **imbalanced** (many more “no” than “yes”)

### 2.2 Bank Customer Churn (Kaggle)

- **Source:** Kaggle – `Customer-Churn-Records.csv`  
- **Task:** Predict whether a bank customer will **churn** (`Exited` = 1) or stay (0).  
- **Type:** Binary classification  
- **Notes:**
  - Contains features such as credit score, geography, age, balance, products, active member, salary, etc.
  - Represents a second, related banking problem – customer retention.

> Datasets are either stored in the `data/` folder or can be downloaded from their original sources and placed there.

---

## 3. Methods and Models

### 3.1 Preprocessing

For both datasets:

- Remove ID-like or leakage-prone features (e.g., `duration` in Bank Marketing)
- Encode target labels as 0/1
- Train/test split with **stratification**
- Preprocessing implemented in **scikit-learn Pipelines**:
  - One-hot encoding for categorical features
  - Scaling of numeric features (where needed)

### 3.2 Models

Bank Marketing (reproduction + extensions):

- Logistic Regression (baseline, as in research paper)
- Decision Tree (as in research paper)
- Additional models explored:
  - k-Nearest Neighbors (KNN)
  - Random Forest
  - Support Vector Machine (SVM)
  - Simple Neural Network (MLP)

Customer Churn (extension):

- Logistic Regression
- Random Forest
- SVM
- Decision Tree

### 3.3 Class Imbalance and SMOTE

For Bank Marketing, the target is imbalanced.  
I test **SMOTE (Synthetic Minority Over-sampling Technique)** with Logistic Regression and compare:

- Logistic Regression (no SMOTE)
- Logistic Regression + SMOTE

The focus is on the impact on **ROC-AUC** and minority-class recall.

---

## 4. Repository Structure

```text
.
├── README.md                         # This file
├── Project Report.pdf                # Final written report (course template)
├── Project Presentation ...          # Slides used in the presentation (PDF or PPTX)
├── data/
│   ├── bank-full.csv                 # Bank Marketing dataset (if included)
│   ├── Customer-Churn-Records.csv    # Churn dataset (if included)
│   └── README.md                     # Links / description of data sources
└── models/
    └── DS301_FinalProject_BankMarketing_MoatazSamara.ipynb
                                      # Jupyter notebook with all code
