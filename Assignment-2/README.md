# ASSIGNMENT-2 README

This notebook builds a machine learning pipeline to predict whether a banking customer will subscribe to an investment product using customer profile, financial, and engagement data from an investment product subscription dataset [1].

## Project overview

The notebook treats the task as a binary classification problem where the target variable is `SubscribedInvestmentProduct` with classes `Yes` and `No` [1]. It loads the dataset, explores its structure, cleans missing values and duplicate rows, preprocesses numerical and categorical variables, trains a Logistic Regression model, and evaluates the model with standard classification metrics [1].

## Dataset

The notebook reads a dataset named `investmentproductsubscriptiondataset.xls` from the same folder as the notebook [1]. The dataset contains 377 rows and 13 columns before duplicate removal, and includes fields such as `Age`, `EmploymentStatus`, `AnnualIncome`, `AccountBalance`, `RiskTolerance`, `PreviousInvestments`, `AdvisorContacted`, `MobileBankingUser`, `FinancialLiteracyScore`, `MarketingEmailOpened`, `NumberofBankProducts`, and the target `SubscribedInvestmentProduct` [1].

## Workflow

### 1. Data loading and inspection

The notebook imports pandas, loads the dataset, displays sample rows, checks dataset shape, and reviews column names, data types, and non-null counts [1].

### 2. Problem definition

The business problem is to help a financial institution predict which customers are likely to subscribe to an investment product, and the machine learning framing is binary classification [1].

### 3. Feature and target selection

`SubscribedInvestmentProduct` is used as the target variable, while `CustomerID` is excluded from the feature set because it is only an identifier [1]. The feature matrix includes demographic, financial, behavior, and engagement variables [1].

### 4. Data cleaning

Missing values are filled using the median for numerical columns and the mode for categorical columns [1]. The notebook also checks for duplicate rows, finds 7 duplicates, removes them, and resets the index, leaving 370 rows after cleaning [1].

### 5. Preprocessing

The notebook uses a `ColumnTransformer` to apply `StandardScaler` to numerical features and `OneHotEncoder` to categorical features, with `handle_unknown="ignore"` for safer encoding during prediction [1].

### 6. Train-test split

The cleaned data is split into training and testing sets using an 80/20 split with `random_state=42` and `stratify=y` to preserve class balance [1]. After splitting, `X_train` has 296 rows and `X_test` has 74 rows [1].

### 7. Model training

The notebook builds a scikit-learn `Pipeline` that combines preprocessing with a `LogisticRegression` classifier using `max_iter=1000` and `random_state=42` [1]. This approach keeps preprocessing and modeling together so the same steps are applied consistently during training and testing [1].

### 8. Evaluation

The model is evaluated using accuracy, precision, recall, F1 score, a confusion matrix, and a classification report [1]. Reported test performance is Accuracy 0.8108, Precision 0.7907, Recall 0.8718, and F1 Score 0.8293, with confusion matrix counts of 26 true negatives, 9 false positives, 5 false negatives, and 34 true positives [1].

## Technologies used

- Python [1]
- pandas [1]
- scikit-learn [1]
- Jupyter Notebook [1]

## How to run

1. Place the notebook and dataset file in the same folder [1].
2. Open `ASSIGNMENT-2.ipynb` in Jupyter Notebook or JupyterLab [1].
3. Make sure the dataset filename matches the notebook code exactly: `investmentproductsubscriptiondataset.xls` [1].
4. Run the cells from top to bottom to reproduce the cleaning, preprocessing, training, and evaluation steps [1].

## Output

Running the notebook produces:
- dataset inspection outputs [1]
- cleaned feature and target sets [1]
- a preprocessing pipeline object [1]
- sample predictions [1]
- a confusion matrix [1]
- evaluation metrics and a classification report [1]
- a results summary table [1]

## Notes

The notebook is designed as an end-to-end beginner-friendly classification workflow with clear step-by-step code and printed outputs for each stage [1]. Because the preprocessing is built into a pipeline, the project follows a good machine learning practice for reproducibility and consistent transformation of training and test data [1].
