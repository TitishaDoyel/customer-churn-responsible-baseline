# ML Problem-Framing Memo: Customer Churn

## 1. Decision and purpose
The proposed use is to identify customers who may be at risk of leaving a service so a human team can review whether helpful support or retention outreach is appropriate.

## 2. Prediction target
- **Target:** `churned`
- **Meaning in this file:** `1` = churned; `0` = did not churn.
- **Unit of observation:** one row per customer record.
- **Prediction/action window:** Not specified in the supplied files. Confirm with the internship mentor or dataset documentation before making a real-world claim.
- **Timing of the target:** The supplied files do not explain when churn was measured relative to the feature values. This must be clarified before deployment.

## 3. Available features
`tenure_months`, `support_tickets`, `monthly_spend_inr`, `last_login_days`, and `plan_type` are candidate input features. `customer_id` is an identifier and should not be used as a predictive feature.

## 4. Non-ML baseline
Use a simple majority-class baseline that predicts the most common class in the training data. Compare any ML model against it. A simple transparent rule can also be discussed, but should not be treated as validated without testing.

## 5. Evaluation plan
Report confusion matrix, precision, recall, F1-score, and balanced accuracy. Explain false positives (unnecessary outreach) and false negatives (missed customers who churn). With only 12 rows, metrics are highly unstable and are for demonstration only.

## 6. Risks and safeguards
- Do not use predictions to deny service, change prices, or penalize customers.
- Keep a human in the decision loop.
- Check data provenance, consent/licensing, and feature timing before any real use.
- Monitor errors and performance on a larger, representative dataset before considering deployment.
- Allow the model to abstain when data are missing, unfamiliar, or confidence is insufficient.

## 7. Current conclusion
The supplied CSV has 12 rows, 7 columns, no missing values, and no duplicate rows. Five records have `churned = 1` and seven have `churned = 0`. All five Basic-plan records are labelled churned, while the Pro and Standard records are labelled not churned. This pattern may reflect a toy/example dataset or a sampling artifact; it must not be generalized to real customers.
