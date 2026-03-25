# 1. Introduction

## 1.1. The Urgency of the Topic

In the problem of fraud transaction detection, the biggest challenge lies not only in the algorithm but also in the nature of the data. The extreme imbalance between legitimate and fraudulent transactions, along with sophisticated behaviors concealed under various payment methods, is a major concern. Machine learning models (such as Random Forest or XGBoost) can only achieve optimal performance when the input data is cleaned and accurately reflects the nature of fraudulent behavior. Therefore, feature engineering, or the process of transforming raw data into meaningful features, helps models understand anomalous patterns and significantly improves their performance.

## 1.2. Project Objectives

Instead of focusing on fine-tuning model parameters, this project focuses on optimizing the quality of input data. Specific objectives include:

**EDA (Exploratory Data Analytics.** Explore hidden relationships between variables to uncover traces of fraudulent behavior on the dataset.

**Feature Engineering.** Constructing new variables from raw data to enhance the algorithm's classification capabilities.

**Evaluate effectiveness.** Perform comparative analysis (A/B testing).aboveThis model demonstrates the importance of data processing. Specifically, in this project, the team will compare the model's performance when trained on raw data versus processed data and feature extraction.

## 1.3. Scope of the Project

The project uses a simulated dataset [PaySim](https://www.kaggle.com/datasets/ealaxi/paysim1?fbclid=IwY2xjawQt4IpleHRuA2FlbQIxMABicmlkETFRQTVMTUtUMEwzR2JFcWZKc3J0YwZhcHBfaWQQMjIyMDM5MTc4ODIwMDg5MgABHt2IJf88BNasTaUnRoEMgKLebwUkbTMWUHinH0pQVV7yfgX2wPPrvsJxk9iN_aem_mbURNxMBhP1k6Iphu4y0XA). Focusing on processes such as data cleaning, EDA, and feature engineering, then using powerful algorithms like Random Forest and XGBoost as measurement tools for verification.

# 2. Dataset Description
## 2.1. Data Structure
Each row in the dataset represents a single financial transaction. The data captures key information such as the transaction timestamp, transaction type, amount, and the account balances of both the sender and the receiver before and after the transaction.

A few sample rows are illustrated below:
#### Sample Transactions
The following examples are extracted from the PaySim dataset to demonstrate the structure of a typical transaction:
| step | type     | amount   | nameOrig     | oldbalanceOrg | newbalanceOrig | nameDest     | oldbalanceDest | newbalanceDest | isFraud | isFlaggedFraud |
|------|----------|----------|--------------|----------------|----------------|--------------|----------------|----------------|--------|----------------|
| 1    | PAYMENT  | 9839.64  | C1231006815  | 170136.0       | 160296.36      | M1979787155  | 0.0            | 0.0            | 0      | 0              |
| 1    | PAYMENT  | 1864.28  | C1666544295  | 21249.0        | 19384.72       | M2044282225  | 0.0            | 0.0            | 0      | 0              |
| 1    | TRANSFER | 181.00   | C1305486145  | 181.0          | 0.0            | C553264065   | 0.0            | 0.0            | 1      | 0              |
| 1    | CASH_OUT | 181.00   | C840083671   | 181.0          | 0.0            | C38997010    | 21182.0        | 0.0            | 1      | 0              |
| 1    | PAYMENT  | 11668.14 | C2048537720  | 41554.0        | 29885.86       | M1230701703  | 0.0            | 0.0            | 0      | 0              |

**Quick observations:**
- Fraudulent transactions (isFraud = 1) often occur in categories such as TRANSFER or CASH_OUT.
- Some transactions result in the sender’s balance dropping to zero immediately — a potentially suspicious pattern that models should learn to detect.

Overall, the dataset does more than store isolated transactions; it captures money flow and balance transitions, which is highly valuable for detecting anomalous behavior.

## 2.2. Feature Explanation
One of the strengths of the PaySim dataset lies in its intuitive and realistic feature design. This allows practitioners not only to train models but also to understand the underlying financial behavior reflected in the data.

The amount variable represents the transaction value and is one of the most critical features. In real-world scenarios, fraudulent transactions often involve unusual amounts — either significantly larger than typical user behavior or deliberately fragmented to avoid detection.

The step variable denotes time in hours, spanning roughly 30 days. This enables time-series analysis, such as identifying accounts that perform multiple transactions within a short period — a common fraud pattern.

Balance-related features, including oldbalanceOrg, newbalanceOrig, oldbalanceDest, and newbalanceDest, are particularly important for modeling money flow. Instead of looking at transactions in isolation, these variables capture the financial state before and after each transaction. For example, an account being drained to zero or a recipient account receiving funds without a clear prior balance can both signal suspicious activity.

Additionally, the type feature categorizes transactions into groups such as PAYMENT, TRANSFER, and CASH_OUT. This is useful because different transaction types carry different risk levels. In practice, TRANSFER and CASH_OUT are more frequently associated with fraudulent behavior than standard payment transactions.

Overall, these features provide not only quantitative data but also behavioral insights, forming a strong foundation for advanced feature engineering in later stages.

## 2.3. Target Variable
In this problem, isFraud serves as the target variable. It defines a binary classification task, where each transaction is labeled as either fraudulent (1) or legitimate (0).

While this may seem straightforward, predicting fraud is inherently challenging. A robust model must not only detect as many fraudulent transactions as possible but also minimize false alarms on legitimate ones. This is especially critical in financial systems, where excessive false positives can frustrate users and erode trust.

In essence, the task involves balancing two competing objectives: maximizing fraud detection (high recall) while maintaining acceptable precision. For this reason, evaluation metrics go beyond accuracy and include precision, recall, and F1-score.

## 2.4. Key Challenge: Class Imbalance
One of the biggest challenges in this dataset is class imbalance. Fraudulent transactions account for only a tiny fraction of the data — typically less than 1% — while the vast majority are legitimate.

This creates a misleading scenario where a model can achieve high accuracy by simply predicting all transactions as non-fraudulent. For instance, if 99% of transactions are legitimate, a model that always predicts 0 will achieve 99% accuracy, yet completely fail at detecting fraud.

As a result, accuracy is not a reliable metric in this context. Instead, recall (fraud detection capability) and F1-score (balance between precision and recall) become far more meaningful. A good model should minimize missed fraud cases, even at the cost of some false positives.

To address this issue, imbalance handling techniques are applied during preprocessing. Oversampling methods such as SMOTE can be used to increase the number of fraud samples, while undersampling reduces the number of legitimate ones. Combining these approaches helps the model better learn patterns from the minority class and improves real-world fraud detection performance.

## 2.5. Preliminary Remarks
Overall, PaySim is a well-structured and accessible dataset with sufficient information to model financial behavior effectively. It serves as a solid foundation for building baseline fraud detection systems.

However, it is important to note that PaySim is a synthetic dataset. As such, fraud patterns may be simplified compared to real-world scenarios. Additionally, it lacks important contextual features such as location, device information, and long-term behavioral history, and it does not fully capture real-time system dynamics.

These limitations should be carefully considered when evaluating the model’s applicability to real-world financial environments.

# 7. Limitations and Future Development Directions

Although the focus on data processing and feature building has significantly improved model performance, the project still faces certain technical hurdles that need to be optimized in the future.

## 7.1. Limitations

**Synthetic Data Bias.** Although PaySim is a high-quality simulated dataset, it still relies on fixed rules. In reality, human fraud behavior is more flexible and unpredictable than automated data generation algorithms, meaning that the generated features may not fully cover all real-world scenarios.

**The scarcity of useful characteristics (Feature Scarcity.** In the original dataset of PaySim, there are a very limited number of columns. In particular, the most important columns are such as `oldbalanceOrg`, `newbalanceOrig`, `oldbalanceDest`, and `newbalanceDest`. These columns often contain direct answers to transactions, such as fraudulent transactions typically draining accounts to zero. Removing or limiting the use of these columns to avoid data leakage leaves too few variables, making it difficult to build a comprehensive model.

**Missing identifying and contextual information (Contextual Data Gap).** The dataset lacks crucial information such as geographical location (IP/GPS), device ID, login history, or the frequency of past transactions by the user. Without this contextual information, relying solely on the amount and type of transaction makes it extremely difficult to distinguish between a large, legitimate transaction and a fraudulent one.

**Reliance on domain expertise.** The techniques employed in this project are primarily based on statistical observations. However, to detect complex forms of money laundering or fraud via social media, the system requires a deeper integration of data and expertise from financial/legal professionals.

## 7.2. Future Improvements

To enhance the value of the data processing workflow, the following areas of improvement will be prioritized:

**Automated Feature Engineering.** Apply tools such asFeaturetoolsor Deep Learning algorithmsAutoencoders) to automatically extract latent features that the human eye or conventional statistical analysis might miss.

**Entity and Relationship Analysis (Graph Features).** Instead of treating each transaction as independent, the future direction will build characteristics based on graphs. Calculating metrics such as node degree or centrality between accounts will help identify organized crime networks.

**Feature Selection Optimization.** Using advanced techniques like SHAP (SHapley Additive exPlanations) or Boruta to remove confounding features, retaining only variables that truly contribute to the model, thereby making the model more streamlined and faster.

**Data/Concept Drift Processing.** Develop a process to monitor changes in data distribution over time. When features no longer retain their original categorical value, the system will automatically trigger a feature reengineering process to adapt to new fraud schemes.

# 9. Conclusion

The project demonstrated that in fraud detection, the features’ quality is just as important as the algorithms themselves. Through the EDA process, we found that fraudulent transactions typically fall into two categories: `TRANSFER` and `CASH_OUT`. And focusing on exploiting the relationships between the few remaining variables helped optimize the model's classification capabilities.

The comparison results show that the model trained on the processed dataset and with feature extraction (Feature Engineering) has superior accuracy (F1-Score) compared to using raw data. The creation of variables such as `isErrorOrg` and `isErrorDest`, has helped the model capture anomalies that individual variables cannot reveal.

A data-centric approach helps businesses better understand customer behavior instead of treating machine learning models as a black box. This allows banks to build rule-based systems combined with AI in a transparent manner, thereby minimizing financial risks and protecting brand reputation.

# References
Lopez-Rojas, E., & Axelsson, S. (2014). PaySim: A financial mobile money simulator for fraud detection.

Kaggle. (n.d.). PaySim dataset. Retrieved from https://www.kaggle.com/datasets/ealaxi/paysim1/data


