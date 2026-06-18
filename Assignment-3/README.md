# Assignment-3
1. Project Overview

This project focuses on building and comparing two machine learning classification models using a selected dataset. The goal is to predict the target variable based on input features and evaluate model performance using different metrics. Logistic Regression and Support Vector Machine (SVM) models were trained and tested to determine which model performs better. The project also explores responsible AI concepts such as bias, limitations, and the importance of human judgment.

2. Dataset

The dataset used in this project is the Investment Product Subscription Dataset. It contains customer-related information used to predict whether a customer will subscribe to an investment product. The dataset includes demographic and financial features that help the machine learning models make predictions.
Dataset Name: investment_product_subscription_dataset.xls
Number of Rows: (check using df.shape)
Number of Columns: (check using df.shape)
Features: Customer-related attributes such as age, income, occupation, account balance, and other financial details.
Target Variable: Subscription status (whether the customer subscribed to the investment product or not).
The dataset was cleaned and preprocessed before training the machine learning models.

3. Machine Learning Workflow

The project followed a standard machine learning workflow:
Loaded and inspected the dataset
Cleaned missing or inconsistent data
Selected features (X) and target variable (y)
Split the dataset into training and testing sets
Applied preprocessing and feature encoding if needed
Trained Logistic Regression and SVM models
Evaluated models using:
Accuracy
Precision
Recall
F1-score
Confusion Matrix

4. Models Used
   
Logistic Regression
A simple and efficient classification algorithm used for predicting categorical outcomes.
Support Vector Machine (SVM)
A supervised machine learning algorithm used for classification by finding the best decision boundary between classes.

6. Results

Both models were evaluated using classification metrics and confusion matrices.
Accuracy was used to measure overall correctness.
Precision measured how many predicted positive cases were actually correct.
Recall measured how many actual positive cases were correctly identified.
F1-score balanced precision and recall.
Confusion matrices helped visualize correct and incorrect predictions.
The model with the higher evaluation scores performed better overall.

7. Interpretation

The results show how machine learning models can help make predictions and support decision-making in real-world business problems. A higher accuracy and F1-score indicate better prediction performance. Recall is especially important when missing positive cases could lead to serious business consequences. These models can improve efficiency, but predictions should still be reviewed carefully.

8. Limitations and Responsible AI Reflection

One limitation of the model is that the dataset may not fully represent real-world situations, which can introduce bias into predictions. If the data is imbalanced, the model may favor one class more than another. Privacy concerns may also arise if sensitive data is used in training.
Human judgment should still be used because machine learning models can make mistakes and may not understand ethical, social, or real-world context. Humans are needed to review predictions and make responsible final decisions.

9. How to Run the Notebook

Open Jupyter Notebook or Google Colab
Upload the dataset file and notebook file

Install required libraries if needed:
pip install pandas numpy scikit-learn matplotlib

Run all notebook cells in order
View model training, evaluation metrics, and results output
