# 🚨 Fraud Detection with Machine Learning  

This project focuses on detecting fraudulent financial transactions using the **Paysim dataset**.  
Fraud detection is a high-stakes problem where missing a fraud (false negative) is much more costly than a few false alarms (false positives).  

---

## 📌 Project Highlights  

- **Custom Feature Engineering**  
  - Transaction count features (`num_transactions_orig`, `num_transactions_dest`)  
  - Ratio features (`amount_to_max_ratio_orig`, `amount_to_max_ratio_dest`)  
  - Time-based features (`day`, `hour`, `day_of_week`)  
  - Log transformation on skewed financial variables  
  - Dropped redundant and ID-like columns (`nameOrig`, `nameDest`, `newbalanceOrig`, `newbalanceDest`, `isFlaggedFraud`)  

- **Modeling**  
  - Tested **Random Forest, XGBoost, LightGBM, and CatBoost**  
  - Final choice: **CatBoostClassifier** for handling categorical + imbalanced data efficiently  
  - Built end-to-end **Pipeline** for clean reproducibility  

- **Hyperparameter Tuning**  
  - Used **Optuna** for parameter search (learning_rate, depth, iterations, L2 regularization, etc.)  
  - Optimized for **PR-AUC (Precision-Recall AUC)** since it’s best for imbalanced datasets  

- **Evaluation Metrics**  
  - Precision, Recall, F1-score  
  - PR-AUC (main metric)  
  - ROC-AUC  
  - Confusion Matrix for error analysis  

---

## ⚙️ Tech Stack  

- **Python**  
- **Libraries**: Scikit-learn, CatBoost, XGBoost, LightGBM, Optuna, Pandas, Matplotlib, Seaborn, SHAP  
- **Pipeline Design** for easy deployment  

---

## 📊 Results  

- **CatBoost (tuned with Optuna)**:  
  - **Recall ~97%** → detects almost all frauds  
  - **High PR-AUC** → excellent performance on rare fraud detection  
  - **Some false alarms (lower precision)** → acceptable trade-off since catching fraud is more critical  

- **Key Features Predicting Fraud**:  
  - Transaction **amount** and **oldbalanceOrg**  
  - Transaction type (`CASH_OUT`, `CASH_IN`)  
  - Time features (`day`, `hour`, `day_of_week`)  

---


