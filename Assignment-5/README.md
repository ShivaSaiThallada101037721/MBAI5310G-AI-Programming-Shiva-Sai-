# FreshCart Plus – Customer Segmentation with K-Means Clustering

## Business Problem

FreshCart Plus is a subscription-based online grocery delivery service facing high customer churn. The company currently sends generic renewal reminders and discounts to all customers, which is inefficient and costly. The core business problem is to identify distinct customer groups based on their behaviour and service experience so that retention strategies can be tailored to each segment rather than applied uniformly. This allows the business to protect high-value customers, recover at-risk customers, and reduce wasted marketing spend.

## Dataset

**File:** `freshcart_subscription_decision_tree_dataset.xlsx`

| Property | Value |
|----------|-------|
| Rows | 360 |
| Columns | 18 |
| Missing values | 6 (imputed with median/mode) |
| Duplicate rows | 0 |

**Numerical features used for clustering:**
- `Months_As_Customer`
- `Monthly_Orders`
- `Avg_Order_Value`
- `App_Sessions_Per_Month`
- `Delivery_Rating`
- `Discount_Usage_Rate`
- `Late_Deliveries_Last_3M`
- `Support_Tickets_Last_3M`
- `Last_Login_Days`
- `Household_Size`
- `Payment_Issues_Last_3M`

## Clustering Method

**Algorithm:** K-Means Clustering  
**Preprocessing:** StandardScaler (z-score normalization)  
**Cluster selection:** Elbow Method (K=1 to K=10 tested)  
**Chosen K:** 4  
**Library:** scikit-learn

The Elbow Method identified K=4 as the natural bend point where the rate of inertia reduction slows significantly. Four clusters also map cleanly to interpretable business segments.

## Main Results

| Cluster | Label | Size | Renewal Rate |
|---------|-------|------|-------------|
| 0 | Passive Low-Spenders | 134 | ~10% |
| 1 | Active At-Risk | 81 | ~15% |
| 2 | High-Value Loyalists | 121 | ~47% |
| 3 | Payment-Friction Customers | 24 | ~17% |

## Business Recommendation

| Segment | Priority Action |
|---------|----------------|
| Cluster 2 – High-Value Loyalists | Protect with loyalty rewards; upsell to premium plans |
| Cluster 1 – Active At-Risk | Service recovery outreach; address delivery quality |
| Cluster 0 – Passive Low-Spenders | Re-engagement campaigns; offer reduced-tier plan |
| Cluster 3 – Payment-Friction | Proactive payment support; flexible billing options |

## Files

```
freshcart_clustering_assignment.ipynb           — Complete Jupyter Notebook (all 7 tasks)
freshcart_subscription_decision_tree_dataset.xlsx — Source dataset
README.md                                       — This file
```

## How to Run

```bash
pip install pandas numpy scikit-learn matplotlib seaborn openpyxl
jupyter notebook freshcart_clustering_assignment.ipynb
```

Ensure the dataset `.xlsx` file is in the same directory as the notebook before running.
