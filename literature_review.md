# Literature Review: Customer Churn Prediction

### Source 1: Verbeke et al. (2012) - *Building classification trees for customer churn prediction*
This study explores rule-based classification models for predicting churn in telecommunications using subscriber demographic and usage data. The authors highlight that tree-based algorithms outperform linear models due to non-linear feature interactions and high robustness against skewness. Their work emphasizes the importance of using evaluation metrics like Area Under the ROC Curve (AUC) rather than raw accuracy due to class imbalance.

### Source 2: Vafeiadis et al. (2015) - *A comparison of machine learning techniques for customer churn prediction*
The paper compares Artificial Neural Networks, Support Vector Machines (SVM), Decision Trees, and Ensemble methods (Random Forest and AdaBoost) across multiple telecom customer datasets. The results show that ensemble models, particularly Boosted Trees, consistently yield superior Precision and Recall compared to single-estimator baselines. The authors conclude that feature scaling and handling missing values correctly are critical steps before training distance-sensitive algorithms like SVMs.

### Source 3: Amin et al. (2019) - *Customer churn prediction in the telecommunication sector using data mining techniques*
This write-up evaluates data preprocessing strategies and feature engineering techniques for retention modeling. The researchers demonstrate that converting raw billing metrics into aggregated interaction variables (e.g., total spend per month relative to total tenure) significantly improves model sensitivity. Additionally, the paper advises using F1-score to balance false positives and false negatives in churn mitigation strategies.