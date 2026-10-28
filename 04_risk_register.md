# Risk Register: Customer Churn Baseline

| ID | Risk | Potential impact | Mitigation / control | Monitoring or rollback trigger |
|---|---|---|---|---|
| R1 | Only 12 rows | Unstable estimates; poor generalization | Treat as educational demo only; obtain a much larger representative dataset | Do not deploy while sample and validation are inadequate |
| R2 | Unknown data provenance and permissions | Privacy, legal, or licensing problems | Document source, collection purpose, permission/consent basis, license, and retention before use | Stop processing if permission or provenance cannot be established |
| R3 | Feature/label timing unclear | Target leakage; misleading scores | Define prediction date and churn horizon; confirm each feature exists before that date | Retrain/evaluate if any feature is measured after the prediction point |
| R4 | False positive | Unnecessary or unwanted outreach | Use respectful optional messages; make it easy to decline; do not penalize customers | Pause outreach if complaints or opt-outs exceed an agreed threshold |
| R5 | False negative | Customers who need help are missed | Keep normal customer support available to everyone; use model only to prioritize optional help | Review missed cases and adjust only after validation |
| R6 | Proxy bias / unequal impact | Some customer groups may be flagged more often or receive worse treatment | Assess group error rates and outreach burden when lawful data and sufficient samples are available | Pause use if a material disparity is detected and not explained/mitigated |
| R7 | Model score treated as certainty | Unfair or inappropriate decisions | Explain uncertainty; human review; supportive use only | Stop use if scores are used for pricing, service denial, or other punitive actions |
| R8 | Data quality changes over time | Degraded performance | Monitor missingness, feature distributions, label rates, and delayed outcome metrics | Investigate drift; revert to non-ML baseline if performance degrades |
| R9 | Customer identifiers exposed | Privacy/security incident | Exclude `customer_id` from model features; limit access; publish only approved data | Restrict access and follow incident process if exposure occurs |

## Fallback and rollback
If data permission is unclear, validation is inadequate, monitoring is unavailable, or material harms are detected, do not launch or pause the model. Use the existing non-ML support process and keep customer support available to all customers.
