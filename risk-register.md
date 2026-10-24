# Risk Register: Customer Churn Training Exercise

| Risk | Why it matters here | Safeguard / mitigation | Trigger to pause or roll back |
|---|---|---|---|
| Tiny, unrepresentative sample | Only 12 records are available. | Obtain larger, representative, documented data before real use. | Any proposal to deploy based on this sample alone. |
| Plan-type shortcut / possible bias | All Basic rows churn and all Pro/Standard rows do not in this file. | Investigate data generation and sampling; compare errors across relevant groups when valid data are available. | Predictions are driven mainly by plan type or harmful group differences appear. |
| Data leakage | Feature timing and churn-label construction are undocumented. | Confirm all features existed before the prediction point; exclude post-outcome information. | Any feature is recorded after the target outcome or target definition is unclear. |
| False positive | A customer who would stay may receive unwanted outreach. | Human review; respectful, low-impact support only. | Complaints or unnecessary contacts rise. |
| False negative | A customer who may leave is missed. | Keep ordinary support available to all; do not rely on model alone. | Miss rates rise or the model misses important cases. |
| Privacy / identifier exposure | `customer_id` identifies individual records. | Exclude ID from model features; restrict access and follow provider policy. | Data are shared publicly without permission or identifiers are exposed. |
| Unclear provenance / permission | Creator, collection process, consent and licence are not stated in the supplied files. | Ask the internship provider for documentation; use only within authorized scope until clarified. | Permission cannot be established for intended use. |
| Performance drift | Customer behavior and service conditions can change. | Monitor data quality and error metrics on an appropriate larger dataset. | Performance or data distributions materially change. |
| Overconfident reporting | Metrics from 12 rows are unstable. | Clearly label results as educational/demo-only; report baseline and sample size. | A small test score is presented as proof of real-world accuracy. |

## Fallback
If provenance, feature timing, data quality, or evaluation is inadequate, do not use model predictions for customer decisions. Use the existing manual/support process while investigating.
