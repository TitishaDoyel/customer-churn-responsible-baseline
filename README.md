# Customer Churn — Responsible ML Baseline

An educational machine learning project exploring customer churn prediction, problem framing, and responsible data practices.

## Project Overview

This project uses a small sample dataset to demonstrate a basic customer churn classification workflow. It compares a majority-class baseline classifier with a logistic regression model and documents the risks and limitations of the exercise.

## Repository Contents

- `customer-churn-training.csv` — Sample dataset used for the exercise.
- `customer_churn_baseline.ipynb` — Data checks, preprocessing, model training, and evaluation.
- `ML-problem-framing-memo.md` — Problem definition and intended use.
- `responsible-data-card-completed.md` — Documentation of the dataset, its context, and limitations.
- `risk-register.md` — Potential risks and mitigation considerations.

## Workflow

1. Load and inspect the dataset.
2. Check missing values, duplicate rows, and target distribution.
3. Separate features from the target and split the data into training and testing sets.
4. Evaluate a majority-class baseline classifier.
5. Train and evaluate a logistic regression pipeline with numerical and categorical preprocessing.

## Results

| Model | Balanced Accuracy |
|---|---:|
| Majority-class baseline | 0.50 |
| Logistic regression | 1.00 |

These results are based on a test set of only four records from a dataset containing 12 rows. The dataset also shows perfect separation of the churn labels by plan type. Therefore, the reported score is highly unstable and must not be interpreted as evidence of real-world predictive performance.

## Responsible Use and Limitations

- The dataset is very small and is intended for educational demonstration.
- The evaluation set is too small to support reliable generalization claims.
- The observed relationship between plan type and churn may not represent real customer behavior.
- The model should not be used for actual customer decisions without appropriate data, validation, fairness checks, and monitoring.

## Tools

- Python
- pandas
- scikit-learn
- Jupyter Notebook

## Purpose

The goal is to demonstrate a beginner-friendly machine learning workflow while emphasizing reproducibility, honest evaluation, problem framing, and responsible data use.
