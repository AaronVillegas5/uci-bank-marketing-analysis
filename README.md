📊 Predicting Marketing Success

By Aaron Villegas

🔍 Overview

This project builds machine learning models to predict whether a customer will subscribe to a term deposit using the UCI Bank Marketing dataset (40,000+ observations).

Two models were developed and compared:

Logistic Regression

Random Forest Classifier

Both models achieved similar performance:

Accuracy: ~83–85%

Recall: ~0.62

While the Random Forest slightly improved precision, Logistic Regression provided stronger interpretability. A combined approach leverages both models: using Random Forest for prediction and Logistic Regression for insight.

🎯 Problem Statement

Banks invest significant resources into marketing campaigns. The goal of this project is to:

Identify customers likely to subscribe to a term deposit

Reduce wasted marketing effort

Improve targeting efficiency

This is a binary classification problem with class imbalance, where predicting subscribers ("yes") is more challenging but more valuable.

📁 Dataset

Source: UCI Bank Marketing Dataset

Size: 40,000+ rows

Target Variable: y (subscription: yes/no)

Features include:

Demographics (age, job, education)

Financial status (loans, default)

Campaign data (previous contact, number of contacts)

Macroeconomic indicators:

Employment variation rate

Euribor interest rate

Consumer price index

Consumer confidence index

🧹 Data Preprocessing

Key steps:

Handled "unknown" values as meaningful categories

Created never_contacted feature from pdays

Replaced pdays = 999 with 0

Dropped duration to prevent data leakage

One-hot encoded categorical variables

Scaled features for Logistic Regression

📊 Exploratory Data Analysis (EDA)

Strong class imbalance (~12% positive class)

Correlation observed among economic indicators → potential multicollinearity

Several features showed moderate correlation with the target

🤖 Models
1. Logistic Regression

Used as a baseline model

Applied StandardScaler via pipeline

Used class_weight='balanced' to address class imbalance

Why Logistic Regression?

Interpretable coefficients

Easy to explain to stakeholders

2. Random Forest Classifier

Handles non-linear relationships

More robust to multicollinearity

Tuned using GridSearchCV

Key hyperparameters tuned:

n_estimators

max_depth

min_samples_leaf

max_features

class_weight

📈 Model Performance
Model	Accuracy	Precision	Recall	ROC AUC	F1 Score
Logistic Regression	0.83	0.34	0.62	0.74	0.44
Cross-Validated Logistic Regression	0.83	0.36	0.63	0.79	0.46
Random Forest (CV)	0.85	0.39	0.62	0.80	0.48
⚖️ Precision–Recall Tradeoff

Recall is prioritized → missing a potential subscriber is costly

Threshold tuning used to:

Increase precision when needed

Balance marketing cost vs effectiveness

🔑 Key Insights
Most Important Features:

euribor3m (interest rates)

emp.var.rate (employment variability)

nr.employed

cons.conf.idx

cons.price.idx

previous contact history

Business Interpretation:

High interest rates → more attractive term deposits

Stable employment → less demand for fixed investments

High inflation → impacts perceived value of deposits

Previously contacted customers are more likely to convert

💡 Final Recommendation

Instead of choosing one model:

👉 Use both models together

Random Forest → make predictions

Logistic Regression → explain decisions

This hybrid approach provides:

Strong predictive performance

Actionable business insights

🚀 Future Improvements

Try advanced models (XGBoost, LightGBM)

Use SMOTE or resampling techniques

Perform feature selection to reduce multicollinearity

Deploy model as an API or dashboard

Incorporate time-based validation

🛠️ Tech Stack

Python

Pandas, NumPy

Scikit-learn

Matplotlib, Seaborn

📌 Conclusion

This project demonstrates how machine learning can:

Improve marketing efficiency

Reduce costs

Provide interpretable insights

By combining predictive power with interpretability, businesses can make smarter, data-driven decisions.
