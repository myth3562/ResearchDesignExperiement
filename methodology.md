# Methodology

## 1. Refined Research Question
Can machine learning models accurately predict customer churn in telecommunications services using account configuration, billing metrics, and demographic data, and which algorithm provides the highest F1-score for identifying high-risk customers?

## 2. Dataset Description
* **Source:** Telecom Customer Dataset (~7,043 rows, 21 attributes).
* **Target Variable:** `Churn` (Binary: `Yes` / `No`).
* **Features:** 
  * *Categorical:* `Gender`, `SeniorCitizen`, `Partner`, `Dependents`, `PhoneService`, `MultipleLines`, `InternetService`, `OnlineSecurity`, `OnlineBackup`, `DeviceProtection`, `TechSupport`, `StreamingTV`, `StreamingMovies`, `Contract`, `PaperlessBilling`, `PaymentMethod`.
  * *Numerical:* `tenure` (months), `MonthlyCharges` ($), `TotalCharges` ($).
* **Dataset Limitations:**
  * Class imbalance: Approximately 26.5% of customers churn, meaning an unadjusted model could achieve ~73.5% accuracy by simply guessing "No".
  * Historical depth: Data represents a static snapshot without detailed month-over-month usage trends over time.

## 3. Data Cleaning Plan
1. **Target Encoding:** Map `Churn` (`Yes` -> 1, `No` -> 0).
2. **Type Casting:** Convert `TotalCharges` from string/object to floating-point numbers.
3. **Missing Value Imputation:** Impute missing `TotalCharges` values (generated when `tenure` = 0) with `0.0`.
4. **Identifier Removal:** Drop `customerID` as it contains no predictive information.

## 4. Feature Engineering Plan
1. **Ratio Features:** Create `AverageMonthlyCost` (`TotalCharges` / `tenure` where `tenure` > 0) to highlight spend trajectory changes.
2. **Service Aggregation:** Create `TotalServices` by summing active add-on subscriptions (`OnlineSecurity`, `OnlineBackup`, `DeviceProtection`, `TechSupport`, `StreamingTV`, `StreamingMovies`).
3. **Categorical Encoding:** One-Hot Encode nominal variables (e.g., `Contract`, `PaymentMethod`, `InternetService`).
4. **Feature Scaling:** Apply `StandardScaler` to continuous features (`tenure`, `MonthlyCharges`, `TotalCharges`, `AverageMonthlyCost`, `TotalServices`) to normalize feature magnitudes.

## 5. Model Selection
* **Model 1: Logistic Regression (Baseline)**
  * *Reasoning:* Highly interpretable, fast to train, and serves as a strong linear benchmark to determine if non-linear patterns exist.
* **Model 2: Random Forest Classifier**
  * *Reasoning:* Capable of capturing non-linear interactions, robust to feature scaling, handles mixed feature types well, and reduces variance through ensemble bagging.

## 6. Evaluation Metrics
* **F1-Score (Primary):** Balances Precision (avoiding false alarms) and Recall (catching true churners). Crucial because class imbalance makes accuracy misleading.
* **ROC-AUC (Secondary):** Evaluates overall class separation capability across all possible decision thresholds.