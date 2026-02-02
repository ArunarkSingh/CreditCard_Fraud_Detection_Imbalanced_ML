# Credit Card Fraud Detection under Extreme Class Imbalance

**Arunark Singh**

---

## Overview

This project builds and evaluates a **credit card fraud detection pipeline** under **extreme class imbalance**, where fraudulent transactions represent less than 0.2% of the data.

Rather than optimizing for misleading accuracy metrics, the focus is on **proper evaluation**, **precision–recall tradeoffs**, and **validation-based threshold tuning** to prioritize fraud recall in realistic screening scenarios.

---

## Key Objectives

- Handle extreme class imbalance responsibly
- Evaluate models beyond accuracy using ROC and Precision–Recall analysis
- Tune the decision threshold based on validation data
- Demonstrate realistic fraud-screening tradeoffs

---

## Dataset

This project uses the **Credit Card Fraud Dataset** from Kaggle.

> **Note:** The dataset is **not included** in this repository due to licensing and privacy considerations.

**How to obtain the data:**
1. Download the dataset from Kaggle
2. Place the file at: data/raw/creditcard.csv

All preprocessing and evaluation steps are fully reproducible using the provided code.

---

## Methodology

### Model
- **Logistic Regression**
- Standardized features using `StandardScaler`
- `class_weight="balanced"` to address imbalance
- Implemented using a clean scikit-learn `Pipeline`

### Data Splitting
- Train / Validation / Test split
- Stratified sampling to preserve class distribution
- Threshold tuning performed **only on validation data**
- Final metrics reported **once on the held-out test set**

---

## Evaluation Strategy

Because fraud detection is highly imbalanced:
- Accuracy alone is misleading
- Precision–Recall analysis is essential
- Recall is prioritized to minimize missed fraud

The following metrics and plots are used:
- Confusion Matrix
- ROC Curve (AUC)
- Precision–Recall Curve (Average Precision)
- Threshold vs Precision/Recall analysis

---

## Validation-Based Threshold Tuning

The default 0.5 decision threshold was replaced with a **validation-selected threshold** to achieve high fraud recall.

- **Chosen threshold:** ~0.48
- **Fraud recall (test):** ~87%
- **Fraud precision (test):** ~5%

This operating point reflects a realistic fraud-screening setup where:
- False positives are acceptable
- Missed fraud is costly
- Downstream review or secondary models may be used

---

## Results Summary (Test Set)

| Metric | Value |
|------|------|
| Fraud Recall | ~87% |
| Fraud Precision | ~5% |
| Accuracy | ~97% |
| Missed Fraud Cases | 12 / 95 |

## Confusion Matrix

|               | Predicted Non-Fraud | Predicted Fraud |
|---------------|--------------------:|----------------:|
| **Actual Non-Fraud** | 55145 | 1506 |
| **Actual Fraud**     | 12    | 83   |
---

## 📊 Visualizations

### Exploratory Data Analysis

#### Transaction Amount Distribution
![Transaction Amount Distribution](analysis_outputs/amount_distribution.png)

#### Feature Correlation Heatmap
![Correlation Heatmap](analysis_outputs/correlation_heatmap.png)

#### Time Distribution (Fraud vs Normal)
![Time Distribution](analysis_outputs/time_distribution.png)

---

### Model Interpretation

#### Top Logistic Regression Features
![Feature Importance](analysis_outputs/feature_importance_lr.png)

---

### Model Evaluation (Threshold Tuned)

#### Normalized Confusion Matrix
![Confusion Matrix](analysis_outputs/confusion_matrix_tuned.png)

#### Precision–Recall Curve
![Precision Recall Curve](analysis_outputs/precision_recall_curve.png)

#### ROC Curve
![ROC Curve](analysis_outputs/roc_curve.png)


## Key Takeaways

- Extreme class imbalance requires careful evaluation beyond accuracy
- Threshold tuning is a critical deployment decision, not a modeling afterthought
- Validation-based threshold selection prevents optimistic bias
- Logistic Regression remains a strong baseline when used thoughtfully

---

## Tech Stack

- Python
- scikit-learn
- Logistic Regression
- NumPy, Pandas
- Matplotlib, Seaborn

---

## Notes on Reproducibility

- Raw and processed datasets are intentionally excluded
- Trained model artifacts are not committed
- All results can be reproduced by running the notebook after downloading the dataset

---

## License

This repository is shared for **educational and portfolio purposes**.


