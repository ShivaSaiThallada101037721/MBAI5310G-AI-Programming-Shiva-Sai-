# MBAI 5310G Decision Tree Classification Assignment

## Project Title

Decision Tree Classification for Marketing Customer Purchase Prediction

## Business Problem

The business wants to predict whether a customer is likely to purchase a product. This prediction supports better marketing decisions by helping the company identify customers who are more likely to respond to campaigns, promotions, and follow-up actions.

## Dataset Description

The dataset is `marketing_customer_purchase.csv`. It contains customer demographic information, geographic information, online behavior, marketing engagement, and purchase outcomes.

The target variable is `Purchased`, with two classes:

- `Yes`: the customer purchased the product
- `No`: the customer did not purchase the product

The input features are:

- `Age`
- `Gender`
- `City`
- `Income`
- `Website_Visits`
- `Time_on_Site_Minutes`
- `Previous_Purchases`
- `Membership_Level`
- `Email_Opened`
- `Discount_Used`
- `Social_Media_Clicks`
- `Cart_Abandoned`

## Machine Learning Workflow

The workflow includes:

1. Loading the dataset
2. Displaying the first five rows
3. Checking dataset shape, column names, data types, missing values, and duplicates
4. Removing duplicate rows
5. Handling missing values
6. Identifying numerical and categorical features
7. Defining `X` and `y`
8. Splitting the data into training and testing sets using an 80/20 split and `random_state=42`
9. Applying One-Hot Encoding to categorical variables
10. Training a Decision Tree Classification model
11. Evaluating the model using confusion matrix, accuracy, precision, recall, F1-score, training accuracy, and testing accuracy
12. Interpreting results from a business perspective
13. Creating visualizations for missing values, target distribution, feature importance, and the confusion matrix

## Decision Tree Model

The assignment uses only a Decision Tree Classifier. The model is trained on preprocessed customer data after categorical variables are converted into numerical format using One-Hot Encoding.

The model configuration used in the notebook is:

```python
DecisionTreeClassifier(max_depth=4, random_state=42)
```

`max_depth=4` keeps the tree easier to interpret and helps reduce overfitting.

## Evaluation Results

According to the Week 4 PDF reference output, the Decision Tree model achieved:

| Metric | Result |
|---|---:|
| Training Accuracy | 0.7921875 |
| Testing Accuracy | 0.725 |
| Accuracy | 0.725 |
| Precision | 0.7777777778 |
| Recall | 0.9032258065 |
| F1-Score | 0.8358208955 |

The reported confusion matrix, using class order `No`, `Yes`, is:

|  | Predicted No | Predicted Yes |
|---|---:|---:|
| Actual No | 4 | 32 |
| Actual Yes | 12 | 112 |

## Business Insights

The Decision Tree performed reasonably well for a simple and interpretable model. The testing accuracy of 72.5% indicates that the model correctly classified most customers in the test set. The recall of 90.3% for the purchaser class is especially useful because it shows that the model identifies most customers who actually purchased.

The most important Decision Tree features reported in the Week 4 PDF are:

1. `Time_on_Site_Minutes`
2. `Income`
3. `Website_Visits`
4. `Cart_Abandoned_Yes`
5. `Social_Media_Clicks`
6. `Age`

These features suggest that website engagement, customer income, shopping intent, social media activity, and age are important signals for predicting purchase behavior.

## Model Limitation

One limitation is class imbalance. The dataset contains more `Yes` purchase cases than `No` cases, which may make the model better at identifying purchasers than non-purchasers. Another limitation is that missing values are imputed using median and mode values, which may simplify the true patterns in the data.

## Conclusion

The Decision Tree Classification model is useful for predicting customer purchase behavior and explaining which features influence the prediction. The model can help the business improve marketing targeting, reduce wasted campaign effort, and prioritize customers with stronger purchase signals. However, the model should be used as decision support rather than a replacement for human judgment because business context, ethical considerations, and changing customer behavior still matter.

## Final Deliverables

- `MBAI_5310_Decision_Tree_Classification.ipynb`: Complete Jupyter Notebook with code, markdown explanations, charts, model training, evaluation, feature importance, and business interpretation.
- `README.md`: Professional project summary covering the business problem, dataset, workflow, model, evaluation results, insights, limitation, and conclusion.

## How to Run

1. Place `marketing_customer_purchase.csv` in the same folder as the notebook.
2. Open `MBAI_5310_Decision_Tree_Classification.ipynb`.
3. Run all cells from top to bottom.
4. Review the generated tables, charts, metrics, and business interpretations.
