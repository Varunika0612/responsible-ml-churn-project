# ML Problem Framing & Responsible Data Card
## Customer Churn Baseline Project

This project explores whether a small customer dataset can support a decision to offer voluntary retention support to customers who may be at risk of leaving.

### Files
- `01_problem_framing_memo.md` — decision, prediction target, intended use, and non-ML baseline.
- `02_responsible_data_card.md` — completed version of the supplied data-card template.
- `03_baseline_notebook.ipynb` — data checks, simple baseline, and an illustrative model.
- `04_risk_register.md` — risks, mitigations, and monitoring/rollback conditions.
- `customer-churn-training.csv` — supplied training data.

### Important limitation
The supplied dataset contains only 12 rows. Any model score will be highly unstable and must not be treated as evidence that the model is ready for real customer decisions. This is a learning/demo baseline only.

### How to run
Open `03_baseline_notebook.ipynb` in Google Colab or Jupyter Notebook. Upload `customer-churn-training.csv` into the same working folder/session, then run the notebook cells from top to bottom. The notebook uses pandas and scikit-learn.

### Data provenance
The source and collection process were not specified in the supplied files. This project does not assume consent, licensing, or representativeness; these must be confirmed before any real-world use.
