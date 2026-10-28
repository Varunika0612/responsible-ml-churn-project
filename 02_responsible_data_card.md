# Responsible Data Card

## Dataset purpose
The dataset may support an educational investigation of whether customer churn can be predicted. If later validated on adequate data, predictions might help offer voluntary retention support. The data must not be used to deny service, change prices, restrict access, or make consequential decisions about individual customers.

## Provenance and permission
The supplied file is named `customer-churn-training.csv`. The files provided with the task do not explain who collected the data, when or how it was collected, whether customers were informed, what consent or other legal basis applies, or what license governs reuse. These details are **unknown and must be verified** before real-world use. Do not claim that consent or a license exists without evidence.

## Population and representation
The file contains 12 rows and 12 unique customer IDs. It has three plan categories (Basic, Standard, Pro). The sampling method, time period, geography, customer demographics, and intended population are not documented. Representativeness cannot be established. The small sample may not capture the variety of customer behavior; group-level fairness cannot be meaningfully assessed from the supplied information.

## Features and target
- `customer_id`: identifier; exclude from model features because it identifies a row rather than providing a meaningful generalizable signal.
- `tenure_months`: customer tenure in months.
- `support_tickets`: recorded support-ticket count; measurement period is unspecified.
- `monthly_spend_inr`: monthly spend in Indian rupees.
- `last_login_days`: days since last login; reference date is unspecified.
- `plan_type`: subscription plan category.
- `churned`: target label, where 1 means churn and 0 means not churn, as interpreted for this exercise; the source does not document the exact label definition or prediction horizon.

Possible leakage risk: feature timestamps and the churn label window are not supplied. Confirm all features were available before the prediction point. Do not use post-churn information. Sensitive attributes are not explicitly present, but plan type, spending, usage, or other features may act as proxies for customer circumstances.

## Quality checks
- Rows: 12; columns: 7.
- Missing values: none in the supplied file.
- Exact duplicate rows: none.
- Duplicate customer IDs: none.
- Target counts: 7 not churned (0), 5 churned (1), or 58.3% / 41.7%.
- Numeric ranges observed: tenure 1–30 months; support tickets 0–5; monthly spend ₹499–₹1,499; last login 1–30 days.
- The small sample means outlier and data-validity checks are limited; observed ranges are not proof that values are correct.
- No train/test split is included in the source. The notebook creates an illustrative stratified split. With only 12 rows, test metrics are extremely uncertain. A real project should use a larger, preferably time-aware holdout and keep customers/periods separated to avoid leakage.

## Risks and safeguards
- **Small sample / poor generalization:** do not deploy; collect a larger representative dataset and validate on later time periods.
- **Unknown provenance and permission:** confirm source, lawful basis/consent where applicable, license, retention, and access controls.
- **False positives:** outreach may annoy customers; make it optional, respectful, and easy to decline.
- **False negatives:** some customers who need support may not be flagged; keep general support available to everyone.
- **Proxy bias:** examine performance and impact across relevant groups if lawful, appropriate data becomes available; do not infer protected traits.
- **Leakage / unclear label window:** define the prediction date and churn horizon; verify all features precede it.
- **Overreliance on score:** human review and supportive actions only; no punitive or high-impact decisions.
- **Privacy/security:** minimize identifiers, restrict access, avoid publishing real personal data, and set retention/deletion rules.

## Intended evaluation
- **Non-ML baseline:** majority-class predictor and/or a transparent support rule; compare model value with the existing process.
- **Performance:** confusion matrix, precision, recall, F1, and accuracy, reported with the class counts and major limitations.
- **Calibration:** assess predicted probabilities only when there is enough data; 12 rows are insufficient for a reliable calibration claim.
- **Fairness:** compare error rates and outreach burden across relevant groups only when appropriate, permitted data and sufficient sample sizes exist. Current data does not support a robust fairness assessment.
- **Error analysis:** inspect false positives and false negatives and the action each would trigger.
- **Decision gate:** no deployment based on this dataset alone; require more data, provenance/permission checks, time-aware validation, monitoring, human review, and rollback criteria.
