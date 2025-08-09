# 🏦 Loan Default Prediction with XGBoost

This project builds a robust binary classification model using XGBoost to predict whether a loan applicant is likely to default. Designed with scalability, interpretability, and risk reduction in mind — it simulates a realistic credit scoring system suitable for financial institutions.

---

## 🚀 Problem Statement

Accurately identifying risky loan applications is vital for lenders to minimize financial exposure. This model assists in predicting loan defaults based on applicant and loan-level features, enabling:
- Flagging borderline cases for manual review
- Preemptive intervention for high-risk approvals
- Strategic loan portfolio assessment

---

## 📂 Dataset Overview

- **Total Samples:** 51,070 applicants
- **Target:** `Default` — Binary (0 = No Default, 1 = Default)
- **Features:** 22 columns
  - **Numerical:** e.g., `Income`, `LoanAmount`, `DebtToIncomeRatio`
  - **Categorical:** e.g., `LoanPurpose`, `EmploymentType`, `HomeOwnership`
- **Preprocessing:**
  - Missing value imputation using median strategy
  - Label encoding for binary columns (e.g., `HasMortgage`, `HasDependents`)
  - Consistent handling of train-test splits to prevent leakage

---

## 📊 Visual Insights

- Class imbalance visualized via bar charts
- Feature importance analysis:
  - Top predictors included: `DebtToIncomeRatio`, `LoanTerm`, `EmploymentLength`, `CreditScore`, and `LoanPurpose`
- Threshold tuning revealed 0.2 as optimal cutoff for maximizing recall without compromising accuracy

---

##⚙️ Model Architecture

- **Algorithm:** XGBoost (`tree_method='hist'`)
- **Objective:** Binary classification (`binary:logistic`)
- **Hyperparameters:**
  - `learning_rate=0.01`
  - `n_estimators=5000`
  - `max_depth=8`
  - `min_child_weight=2`
  - `subsample=0.95`
  - `colsample_bytree=0.95`
  - `gamma=0.5`
  - `reg_alpha=0.1`
  - `reg_lambda=2.0`
- **Calibration:** Optional isotonic calibration post-fit

---

## 📈 Performance Metrics

- **Accuracy:** 88.77% (at optimal threshold of 0.5)
- **ROC AUC:** 0.748
- **Confusion Matrix @ threshold 0.2:**

- **Interpretation:**
- Recalls ~42% of actual defaulters
- Maintains precision in non-default predictions
- Balances false positives with acceptable trade-off

---

## 💡 Business Value

This model can:
- Reduce approval of high-risk loans
- Prioritize manual reviews for borderline applications
- Complement existing credit scoring systems

Even a 1% lift in predictive accuracy could prevent hundreds of bad loans, saving substantial financial capital.

---

## 📌 Future Work

- Deploy model via FastAPI or Streamlit for real-time scoring
- Test model drift on newer loan cohorts
- Enhance fairness metrics across demographic segments
