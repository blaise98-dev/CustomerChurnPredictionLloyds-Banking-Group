# CustomerChurnPredictionLloyds-Banking-Group
Data science graduate project at Lloyds Banking Group focused on predicting customer churn through data gathering, exploratory analysis, preprocessing, and machine learning modeling to enhance customer retention.

## 📦 Section 1: Data Gathering & Integration

### 📖 1.0 Introduction
This report aims to understand customer behavior and identify drivers of churn through data integration and exploratory analysis.

**Objectives:**
- Identify churn-related features
- Analyze customer behavior and usage patterns
- Prepare data for ML modeling

### 📁 1.1 Data Sources
Data merged from multiple Excel sheets:

| Sheet Name      | Description                                 | Records |
|-----------------|---------------------------------------------|---------|
| Demographics     | Age, Gender, Income Level                   | 1000    |
| Transactions     | Purchase history & spend data              | 5054    |
| Interactions     | Customer support contacts                   | 1002    |
| Usage            | Login behavior & service usage             | 1000    |
| Churn            | Churn labels                               | 1000    |

### ✅ 1.2 Integration Rationale
- Combined features offer a holistic customer view
- Data joined using consistent customer ID (row index)
- Churn column used as the target variable

### 📌 1.3 Selected Features

| Data Area        | Key Features                             | Purpose                                  |
|------------------|-------------------------------------------|------------------------------------------|
| Demographics     | Age, Gender, Income Level                | Customer profiling                       |
| Transactions     | AmountSpent, ProductCategory             | Spending patterns                        |
| Interactions     | InteractionType, ResolutionStatus        | Service quality & satisfaction           |
| Usage            | LastLoginDate, LoginFrequency            | Engagement indicator                     |
| Churn            | ChurnStatus                              | Target label                             |

---

## 🔍 Section 2: Exploratory Data Analysis (EDA)

### 📊 2.1 Dataset Summary
- Total Records: 5054
- Labeled Churn: 1000 (20%)
- Total Columns: 14
- Missing Data: Present across Demographics, Interactions & Usage

### 📉 2.2 Missing Values Overview
| Feature Group     | Missing Data Pattern                       |
|-------------------|--------------------------------------------|
| Demographics       | ~80% missing (mostly nulls)               |
| Usage & Interactions | High missing rate (>75%)               |
| Transactions       | Complete                                  |
| Churn              | Only 1000 labeled records                 |

### 📈 2.3 Key Visual Insights
- **Age**: Younger customers churn more
- **AmountSpent**: Low spenders are more likely to churn
- **LoginFrequency**: Strong inverse relation with churn
- **IncomeLevel**: Low-income = higher churn
- **ServiceUsage**: Basic users churn more
- **ResolutionStatus**: Unresolved cases increase churn
- **Gender**: Slightly higher churn in females

### 🧩 2.4 Correlation Matrix
- `LoginFrequency` & `AmountSpent`: Negatively correlated with `ChurnStatus`
- `Age`: Weak correlation

### 🌟 2.5 Top Churn Indicators

| Feature          | Key Insight                                      |
|------------------|--------------------------------------------------|
| Age              | Younger/older segments more prone to churn       |
| AmountSpent      | High spend = higher retention                    |
| LoginFrequency   | Fewer logins = disengagement = churn             |
| ResolutionStatus | Pending issues increase churn likelihood         |
| ServiceUsage     | Premium services = lower churn                   |

### ✅ 2.6 Summary Observations
- **Churn Rate**: 20% (imbalanced)
- **Engagement Features**: Highly informative
- **Data Gaps**: Affects completeness of modeling

---

## 🧹 Section 3: Data Cleaning & Preprocessing

### ✅ 3.1 Steps Taken
1. **Missing Values**
   - Dropped rows with missing values in critical fields
   - Retained only fully labeled & complete records (1000 rows)

2. **Outlier Handling**
   - Mild outliers kept
   - Extreme values capped using percentiles (1st & 99th)

3. **Feature Scaling**
   - Applied `StandardScaler` to: `Age`, `AmountSpent`, `LoginFrequency`

4. **Categorical Encoding**
   - One-hot encoded: `Gender`, `MaritalStatus`, `IncomeLevel`, etc.

---

✅ **Ready for Modeling Phase**: Dataset now consists of 1000 clean, labeled records with key predictors standardized and categorical values encoded.

## 4. Model Training and Evaluation

The Random Forest model was trained using the preprocessed data and optimized through hyperparameter tuning using GridSearchCV with 5-fold cross-validation. The best parameters were:
**{'max_depth': 10, 'min_samples_leaf': 1, 'min_samples_split': 2, 'n_estimators': 200}`**

**Performance Metrics:**

The model's performance was evaluated using the following metrics:

* **Accuracy:** Overall correctness of predictions.
* **Precision:** Proportion of correctly identified churners out of all predicted churners.
* **Recall:** Proportion of correctly identified churners out of all actual churners.
* **F1-score:** Harmonic mean of precision and recall, balancing both metrics.
* **AUC:** Area Under the Curve of the ROC (Receiver Operating Characteristic) curve, measuring the model's ability to distinguish between classes.

**Evaluation Results:**

![alt text](image-1.png)

### Feature Importance:

To gain insights into which factors contributed most to churn prediction, we analyzed feature importance using the fitted Random Forest model. The chart below shows the top features that significantly influenced the model's decisions:

![Feature Importance](aa4124ff-87a7-4585-8677-c322f4af65c8.png)

#### Key Observations:

- **Gender_M** and **IncomeLevel_Low** were the most important predictors, highlighting potential demographic trends.
- **Service usage**, such as **Online Banking** and **Website Interactions**, had significant influence, suggesting behavioral patterns matter.
- Features like **AmountSpent**, **LoginFrequency**, and **LastLoginDate_Days** indicate that customer engagement levels are vital indicators of churn.
- Demographics (e.g., **Age**, **MaritalStatus**) and service feedback (**InteractionType_Feedback**, **ResolutionStatus_Unresolved**) also play a role.


## 5. Business Applications and Recommendations

**Utilizing the Model's Predictions:**

* **Customer Segmentation:** Identify high-risk customers based on their churn probability scores.
* **Targeted Retention Campaigns:** Design personalized retention strategies for high-risk segments.
* **Proactive Customer Service:** Offer proactive support to customers with high churn likelihood.
* **Product and Service Improvements:** Understand factors driving churn and improve offerings accordingly.

**Potential Areas for Improvement:**

* **Explore More Features:** Include additional relevant data sources, such as customer feedback or website interactions.
* **Refine Feature Engineering:** Experiment with different feature transformations or combinations.
* **Ensemble Methods:** Consider combining the Random Forest model with other strong models for potentially better performance.
* **Continuous Monitoring:** Track model performance over time and retrain as needed.

## 6. Conclusion

The Random Forest model provides a valuable tool for predicting customer churn at Lloyds Banking Group. By leveraging its predictions, the business can implement data-driven strategies to reduce churn and enhance customer retention. However, continuous monitoring and refinement are crucial to ensure long-term effectiveness. 



