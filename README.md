# Bank Marketing Classification Model Comparison

## Overview

This project analyzes a bank telemarketing dataset to predict whether a customer will subscribe to a term deposit. The focus is on comparing multiple classification models and identifying the best approach based on business objectives.

---

## Business Objective

The goal is to improve the effectiveness of telemarketing campaigns by identifying customers who are most likely to subscribe to a term deposit.

By doing so, the bank can:

* Increase conversion rates
* Reduce unnecessary calls
* Optimize marketing resources

---

## Dataset

* Source: UCI Machine Learning Repository (Bank Marketing Dataset)
* Records: ~41,000 customer observations
* Target Variable: `y` (yes/no subscription)

### Feature Categories:

* Customer information (age, job, marital status, education)
* Financial attributes (loan, housing, default)
* Campaign details (contact type, campaign count, previous outcomes)
* Economic indicators

---

## Problem Type

Binary classification:

* `1` → Customer subscribes
* `0` → Customer does not subscribe

---

## Data Preparation

* Converted target variable (`y`) to binary (1/0)
* Applied one-hot encoding for categorical variables
* Removed `duration` feature to avoid data leakage
* Split dataset into training (80%) and testing (20%)

---

## Baseline Model

* Baseline accuracy: ~88.7%
* Achieved by predicting all customers as "no"
* Indicates strong class imbalance

---

## Models Evaluated

### Default Models (Accuracy-Based)

| Model               | Test Accuracy |
| ------------------- | ------------- |
| Logistic Regression | ~0.897        |
| SVM                 | ~0.895        |
| KNN                 | ~0.887        |
| Decision Tree       | ~0.840        |

Logistic Regression performed best when evaluated using accuracy.

---

## Class Imbalance Insight

* ~89% of customers do not subscribe
* ~11% subscribe

Accuracy alone is misleading in this scenario.

---

## Model Improvement (Recall-Based Evaluation)

Models were tuned using GridSearchCV and evaluated using recall.

### Tuned Model Performance

| Model               | Recall | Precision | F1 Score |
| ------------------- | ------ | --------- | -------- |
| Decision Tree       | ~0.34  | ~0.31     | ~0.33    |
| KNN                 | ~0.30  | ~0.41     | ~0.35    |
| Logistic Regression | ~0.21  | ~0.64     | ~0.32    |
| SVM                 | ~0.20  | ~0.61     | ~0.30    |

---

## Key Findings

### 1. Metric Selection Changes Model Choice

* Logistic Regression is best for accuracy
* Decision Tree is best for recall

### 2. Tradeoff Between Precision and Recall

* Decision Tree → higher recall (captures more subscribers)
* Logistic & SVM → higher precision (fewer false positives)

### 3. Best Model for Business Use Case

Decision Tree is the most suitable model because it identifies the highest number of potential subscribers.

---

## Recommendations

### Targeting Strategy

* Use Decision Tree model to prioritize customers for outreach
* Focus on maximizing recall to avoid missing potential subscribers

### Campaign Optimization

* Accept some false positives to improve overall conversion
* Continuously refine targeting strategy using updated data

### Future Improvements

* Apply class balancing techniques (e.g., SMOTE)
* Tune classification thresholds
* Explore ensemble models such as Random Forest

---

## Conclusion

This project demonstrates that model evaluation must align with business goals. While Logistic Regression performs well in accuracy, the Decision Tree model is more effective for this use case due to its higher recall, making it better suited for improving marketing outcomes.

---

## Project Structure

* `prompt_III.ipynb` → Main notebook
* `data/bank-additional-full.csv` → Dataset
* `README.md` → Project summary

---
