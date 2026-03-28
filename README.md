# 📊 Predicting Marketing Success
**By Aaron Villegas**

---

## 🔍 Overview
This project predicts whether a customer will subscribe to a term deposit using the **UCI Bank Marketing Dataset** (40,000+ observations).

Two models were developed and compared:

- **Logistic Regression** – interpretable, baseline model  
- **Random Forest Classifier** – robust, non-linear model

**Performance Highlights:**

- Accuracy: ~83–85%  
- Recall: ~0.62  

> **Hybrid approach:** Use Random Forest for prediction and Logistic Regression for interpretability and actionable insights.

---

## 🎯 Problem Statement
Banks spend significant resources on marketing campaigns. Goals of this project:

1. Identify customers likely to subscribe  
2. Reduce wasted marketing effort  
3. Improve targeting efficiency  

This is a **binary classification problem with class imbalance**—predicting subscribers (“yes”) is challenging but more valuable.

---

## 📁 Dataset
- **Source:** UCI Bank Marketing Dataset  
- **Size:** 40,000+ rows  
- **Target Variable:** `y` (subscription: yes/no)  
- **Features:**  
  - **Demographics:** age, job, education  
  - **Financial status:** loans, default  
  - **Campaign info:** previous contact, number of contacts  
  - **Macroeconomic indicators:**  
    - Employment variation rate  
    - Euribor interest rate  
    - Consumer price index  
    - Consumer confidence index  

---

## 🧹 Data Preprocessing
Key steps:

- Treated `"unknown"` values as meaningful categories  
- Created `never_contacted` feature from `pdays`  
- Replaced `pdays = 999` with `0`  
- Dropped `duration` to prevent data leakage  
- One-hot encoded categorical variables  
- Scaled features for Logistic Regression  

---

## 📊 Exploratory Data Analysis (EDA)
- Strong class imbalance (~12% positive class)  
- Correlations among economic indicators → potential multicollinearity  
- Several features moderately correlated with target  

---

## 🤖 Models

### 1️⃣ Logistic Regression
- Baseline model  
- StandardScaler via pipeline  
- `class_weight='balanced'` to handle imbalance  
- **Pros:** Interpretable coefficients, easy to explain to stakeholders  

### 2️⃣ Random Forest Classifier
- Handles non-linear relationships  
- Robust to multicollinearity  
- Tuned via GridSearchCV: `n_estimators`, `max_depth`, `min_samples_leaf`, `max_features`, `class_weight`  
- **Pros:** Higher predictive performance  

---

## 📈 Model Performance

| Model                          | Accuracy | Precision | Recall | ROC AUC | F1 Score |
|--------------------------------|---------|-----------|--------|--------|----------|
| Logistic Regression             | 0.83    | 0.34      | 0.62   | 0.74   | 0.44     |
| Cross-Validated Logistic Reg.   | 0.83    | 0.36      | 0.63   | 0.79   | 0.46     |
| Random Forest (CV)              | 0.85    | 0.39      | 0.62   | 0.80   | 0.48     |

**Precision–Recall Tradeoff:**  
- Recall is prioritized → missing a potential subscriber is costly  
- Threshold tuning balances marketing cost vs. effectiveness  

---

## 🔑 Key Insights
**Most Important Features:**

- `euribor3m` (interest rates)  
- `emp.var.rate` (employment variability)  
- `nr.employed`  
- `cons.conf.idx`  
- `cons.price.idx`  
- Previous contact history  

**Business Interpretation:**

- High interest rates → more attractive term deposits  
- Stable employment → less demand for fixed investments  
- High inflation → impacts perceived value of deposits  
- Customers previously contacted → higher conversion likelihood  

---

## 💡 Final Recommendation
**Hybrid approach:**  

- **Random Forest** → predictions  
- **Logistic Regression** → interpretability  

**Benefits:**  

- Strong predictive performance  
- Actionable business insights  

---

## 🚀 Future Improvements
- Try advanced models (XGBoost, LightGBM)  
- Apply SMOTE or other resampling techniques  
- Feature selection to reduce multicollinearity  
- Deploy as an API or interactive dashboard  
- Incorporate time-based validation  

---

## 🛠️ Tech Stack
- Python, Pandas, NumPy  
- Scikit-learn  
- Matplotlib, Seaborn  

---

## 📌 Conclusion
This project demonstrates how machine learning can:  

- Improve marketing efficiency  
- Reduce costs  
- Provide interpretable insights  

> Combining predictive power with interpretability allows businesses to make smarter, data-driven decisions.
