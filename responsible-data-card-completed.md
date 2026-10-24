# Responsible Data Card

## Dataset purpose
This small training dataset may support a learning exercise about customer churn prediction and responsible ML. It must not be used by itself to make consequential decisions about real customers, deny services, set prices, or penalize customers. Any retention outreach should be reviewed by a person.

## Provenance and permission
The provided file is named `customer-churn-training.csv`. The supplied template and CSV do not identify the original creator, collection method, licensing terms, consent status, or whether the records are synthetic. These details are **unknown** and should be confirmed with the internship provider before sharing or using the data outside this exercise. Do not assume consent or a licence that is not documented.

## Population and representation
The CSV contains 12 customer records. The sampling method and population represented are not documented. Class counts are 7 non-churned records (`churned = 0`) and 5 churned records (`churned = 1`). All five Basic-plan records are churned, and all Pro/Standard records are not churned. This perfect association in a tiny sample raises a serious representativeness and generalization concern. The dataset does not provide demographic or other group information needed for a broader fairness assessment.

## Features and target
- `customer_id`: record identifier; exclude from model inputs.
- `tenure_months`: tenure in months; verify when it was measured.
- `support_tickets`: number of support tickets; verify the counting window and whether it precedes the target outcome.
- `monthly_spend_inr`: monthly spend in INR; verify the measurement period.
- `last_login_days`: days since last login; verify when this was measured.
- `plan_type`: plan category (Basic, Standard, Pro); may strongly drive predictions in this sample and could act as a proxy for customer segments.
- `churned`: target label; 1 means churned and 0 means not churned in this file.

Potential leakage: the files do not describe feature timestamps or how the churn label was created. Confirm that every input feature was available before the prediction point and does not include information recorded after churn. Do not train on `customer_id`.

## Quality checks
- Rows: 12; columns: 7.
- Missing values: 0 in all columns.
- Exact duplicate rows: 0.
- Numeric ranges observed: `tenure_months` 1–30; `support_tickets` 0–5; `monthly_spend_inr` ₹499–₹1,499; `last_login_days` 1–30.
- Target balance: 7 not churned (58.3%); 5 churned (41.7%).
- Outliers: the small sample is too limited to decide whether any value is truly anomalous; validate values with domain documentation.
- Train/test separation: use a fixed random seed and hold out data before fitting preprocessing/model steps. Because the dataset has only 12 rows, any split-based score is very unstable and should be treated as a demonstration, not evidence of production readiness.

## Risks and safeguards
- **Overfitting / unrepresentative sample:** use more representative data; report sample size and uncertainty.
- **False positives:** a customer may receive unnecessary contact. Keep outreach respectful and human-reviewed.
- **False negatives:** a customer at risk may be missed. Do not rely on the model as the only support channel.
- **Bias / proxy risk:** `plan_type` completely separates the labels in this sample. Investigate this pattern and evaluate fairness on appropriate, lawfully available data before real use.
- **Privacy:** customer identifiers can be sensitive. Minimize access, remove identifiers from modeling, and follow the provider's data-handling rules.
- **Misuse:** never use this small model to deny service, change prices, or penalize customers.
- **Monitoring / rollback:** stop using the model if data quality changes, error rates rise, or harmful differences appear; return to the non-ML/manual process and investigate.

## Intended evaluation
Before training, compare:
1. A majority-class `DummyClassifier` baseline.
2. A simple Logistic Regression pipeline with categorical encoding and numeric features.

Report confusion matrix, precision, recall, F1-score, and balanced accuracy. Examine false positives and false negatives separately. If reliable probability estimates are available on a sufficiently large dataset, assess calibration. Fairness evaluation requires appropriate group information and a defensible evaluation plan; this CSV alone is insufficient. Any score on 12 records is illustrative only.
