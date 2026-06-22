# Assignment 6: Model Evaluation, Explainability, and Fairness Reflection

**Course:** MBAI 5310G: AI Programming – Ontario Tech University
**Dataset:** SaaS Free Trial User Conversion Dataset
**Model:** Decision Tree Classifier (scikit-learn)

---

## Dataset Description

The dataset contains records of SaaS free-trial users and their behaviour during a trial period.
It includes 400 records and 17 columns covering demographics (age, age group, gender, region),
company details (company size, user role), trial behaviour (logins, features used, team invites,
support tickets, webinar attendance, trial length), and satisfaction signals (satisfaction score,
days since last login). The dataset has no significant missing values or duplicates.

| Group | Columns |
|---|---|
| Identifier (removed) | `user_id` |
| Demographics | `age`, `age_group`, `gender`, `region` |
| Company | `company_size`, `user_role` |
| Trial Behaviour | `trial_length_days`, `logins_during_trial`, `features_used_count`, `team_members_invited`, `support_tickets`, `webinar_attended` |
| Satisfaction | `trial_satisfaction_score`, `days_since_last_login` |
| **Target** | **`converted_to_paid`** (1 = converted, 0 = did not convert) |
| Kept only for fairness reflection | `gender`, `age_group`, `region` |

---

## Target Variable

The target variable is **`converted_to_paid`**: **1** means the user converted to a paid plan
and **0** means they did not. The dataset is moderately imbalanced, with more converted users
than non-converted users, which means accuracy alone may not fully capture model performance —
precision, recall, and F1-score must also be considered.

---

## Model Used

A **Decision Tree Classifier** (`max_depth=4`, `random_state=42`) trained on an 80/20
stratified train/test split. The identifier column (`user_id`) was removed before training.
The fairness columns (`gender`, `age_group`, `region`) were held aside and **not** used as
model inputs. All categorical features were one-hot encoded, producing 20 numerical input
features. The notebook also applies 5-fold cross-validation, tests tree depths from 1–10 to
analyze overfitting, and explains predictions using feature importance, SHAP, and LIME.

---

## Main Evaluation Results

| Metric (Test Set) | Score |
|---|---:|
| Accuracy | 0.7692 |
| Precision | 0.8333 |
| Recall | 0.8000 |
| F1-Score | 0.8163 |

| Confusion Matrix | Predicted Not Converted | Predicted Converted |
|---|---:|---:|
| **Actual Not Converted** | 20 (TN) | 8 (FP) |
| **Actual Converted** | 10 (FN) | 40 (TP) |

| Tree Variant | Training Accuracy | Testing Accuracy | Gap |
|---|---:|---:|---:|
| Controlled (`max_depth=4`) | 0.8718 | 0.7692 | 0.1026 |
| Deep (`max_depth=10`) | 1.0000 | 0.7436 | 0.2564 |

- **Cross-validation:** 5-fold mean accuracy ≈ 0.74, standard deviation ≈ 0.015 — model is stable.
- **Overfitting:** Mild at depth 4; strong at depths 8+, where training accuracy hits 1.00 but
  testing accuracy drops to 0.74.
- **Top features:** `days_since_last_login`, `logins_during_trial`, `features_used_count`,
  `team_members_invited`, `trial_satisfaction_score`.

---

## Main Business Interpretation

The model predicts whether a free-trial user will convert to a paid subscription. At 76.92%
accuracy and 80% recall, it correctly identifies the large majority of real converters and can
be used to prioritise sales or customer success outreach during the trial window.

The most costly error is **false negatives** (10 users) — actual converters the model missed,
meaning potential revenue goes untargeted. SHAP and LIME analysis confirm that recent login
activity, depth of feature usage, and team invitations are the strongest individual-level
conversion signals — all real-time in-product behaviours the business can monitor.

A fairness check reveals accuracy gaps across groups (e.g., East region 85.7% vs. South region
70.8%; age group 26–35 reaches 88.9% vs. 70.4% for the 51+ group), which should be reviewed
before the model is used for personalised targeting to avoid systematically under-serving
certain customer segments.

**Final recommendation:** This model is a **promising early prototype**. Before full deployment,
it should be validated on a larger dataset, have its decision threshold tuned to reflect the
business cost of false negatives vs. false positives, and be benchmarked against Logistic
Regression and Random Forest. It should support — not replace — human judgment in sales and
customer success decisions.

---

## One Limitation of the Model

The model relies entirely on behavioural signals recorded during the trial. This means it
performs well for active users but may not generalise to users who signed up and became
immediately inactive — a critical and common segment in free-trial funnels. Additionally,
even though `gender`, `age_group`, and `region` were excluded as model inputs, these groups
can still be indirectly encoded in behavioural features, and the fairness analysis confirms
uneven accuracy across groups. Continuous fairness monitoring is essential before any
targeted deployment.

---

## Files
## Files
assignment-6/
├── Assignment-6.ipynb # Main Jupyter Notebook
├── Assignment-6.pdf # PDF version of the notebook
├── dataset.csv # Free trial user dataset
└── README.md # This file

text

---

## How to Run

```bash
pip install pandas numpy scikit-learn matplotlib seaborn shap lime jupyter
jupyter notebook Assignment-6.ipynb
```

Run all cells in order from top to bottom. The dataset CSV must be in the same folder
as the notebook.

---
