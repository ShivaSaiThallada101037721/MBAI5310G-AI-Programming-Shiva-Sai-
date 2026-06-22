# Assignment 8: Natural Language Processing Pipeline and Text Classification

**Course:** MBAI 5310G: AI Programming – Ontario Tech University  
**Dataset:** Insurance Customer Message Classification Dataset (Dataset 13)  
**Company Context:** SafeShield Insurance  
**Model:** Text Classification using NLP Pipeline

---

## Business Problem

SafeShield Insurance receives customer messages every day through multiple channels — email, chat, mobile app, claims portal, and call transcripts. This project builds an NLP text classification model that automatically reads a customer message and predicts which category it belongs to, allowing SafeShield to route messages instantly and reduce response time.

---

## Dataset Description

120 customer messages across 6 balanced categories. Columns: MessageID, MessageDate, Channel, City, PolicyType, CustomerType, **CustomerMessage** (main text column), **MessageCategory** (target), UrgencyLevel.

---

## Target Variable

**MessageCategory** — 6 classes, 20 records each:
Auto_Claim, Home_Claim, Travel_Claim, Policy_Question, Payment_Issue, Document_Request.

---

## Model Used

Decision Tree / Naive Bayes / Logistic Regression / Random Forest on TF-IDF or Bag of Words features. 80/20 train/test split.

---

## Main Evaluation Results

Evaluated using Accuracy, Precision, Recall, F1-Score, and Confusion Matrix.

---

## Business Interpretation

The model routes incoming insurance messages to the correct team automatically. Claim messages contain action words (cracked, leaked, denied); policy/document messages use question language (explain, cover, send). Automating routing reduces triage time for urgent High-priority messages.

---

## One Limitation

Only 120 records (20 per class). Overlapping vocabulary (e.g., "claim" across Auto, Home, Travel) makes category separation difficult. Needs more data for production use.

---

## How to Run

pip install pandas numpy scikit-learn matplotlib seaborn nltk openpyxl jupyter  
jupyter notebook Assignment-8.ipynb

---

