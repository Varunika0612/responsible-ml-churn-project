# ML Problem-Framing Memo: Customer Churn

## 1. Decision to support
A subscription service may use this analysis to decide which customers should be offered a voluntary, low-risk retention check-in or information about available support.

## 2. Prediction target
- **Target:** `churned`
- **Meaning in the supplied file:** 1 indicates churn; 0 indicates no churn.
- **Unit of observation:** one row per customer, represented by `customer_id`.
- **Prediction time/action window:** not specified in the source data. Before real deployment, define the date on which each feature is measured and the future period in which churn is predicted. Do not use information recorded after the prediction time.

## 3. Why ML might help
A model could combine tenure, support-ticket count, monthly spend, recent-login timing, and plan type to prioritize which customers receive an optional check-in. This is a hypothesis to test, not a proven benefit.

## 4. Non-ML baseline
Start with a simple rule such as offering the same standard support message to all customers, or using a transparent rule based on a recent lack of login. Compare any model against this baseline for usefulness, cost, and customer impact. Do not assume the model is better just because it has a score.

## 5. Intended and prohibited use
**Potential intended use:** internal analysis and a voluntary, supportive outreach offer after validation.

**Must not be used for:** denying service, increasing prices, restricting account access, making contractual decisions, or treating a risk score as proof that a customer will leave.

## 6. Error costs and evaluation
- **False positive:** model flags a customer who would not churn; possible cost is unnecessary outreach or annoyance.
- **False negative:** model misses a customer who does churn; possible cost is a missed opportunity to provide support.
- Track precision, recall, F1, confusion matrix, and the share of customers flagged. Compare with the non-ML baseline. If the model is used to rank outreach, evaluate the actual benefit and burden of outreach as well as predictive metrics.

## 7. Readiness decision
The dataset has only 12 rows, and its collection process, time period, population, and label definition are undocumented. It is suitable only for a small educational demonstration. It is not sufficient for a reliable deployment decision. Obtain documented provenance, permission, a larger representative dataset, time-aware train/test separation, and stakeholder review before considering real use.
