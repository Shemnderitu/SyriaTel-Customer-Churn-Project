
![Customer Churn Prediction at SyriaTel](https://github.com/Shemnderitu/SyriaTel-Customer-Churn-Project/blob/master/images/Customer%20Churn%20Prediction%20at%20SyriaTel.png)

# 📊 Customer Churn Prediction at SyriaTel

## 📌 Overview

Customer churn represents one of the most significant challenges in the telecom industry. High churn rates lead to revenue loss and increase the costs associated with acquiring new customers. This project focuses on developing a predictive model that identifies customers likely to churn based on historical usage data and service interactions. With this model, SyriaTel can implement early intervention strategies to retain valuable customers and enhance service quality.

---

## 🧠 Business and Data Understanding

### 🧪 Business Problem
- SyriaTel wants to understand and reduce customer churn. The company needs a way to identify customers who are likely to leave so that appropriate interventions can be applied (e.g. loyalty programs, special offers).

### 👥 Stakeholders

- **Customer Retention and Marketing Teams**: Require churn predictions to target high-risk customers with tailored offers and support.
- **Executive Team**: Needs churn metrics and modeling insights to inform strategic initiatives and business decisions.

### 🎯 Business Objective

To minimize customer attrition by predicting churn risk and offering proactive solutions. Early identification allows the business to reduce churn, increase revenue stability, and improve customer lifetime value.

### 📊 Data Understanding

The dataset in use was obtained from [kaggle](https://www.kaggle.com/datasets/becksddf/churn-in-telecoms-dataset?resource=download).
The dataset contains 3,333 customer entries and 20+ features, including:

- **Demographic attributes**: e.g., state, area code
- **Subscription details**: international plan, voice mail plan
- **Service usage**: total minutes, calls, and charges across time periods
- **Support history**: number of customer service calls
- **Target**: churn (boolean, True/False)

The data required preprocessing steps such as encoding categorical features, detecting multicollinearity (e.g., between minutes and charges), and handling class imbalance.

---

## 🔍Exploratory Data Analysis

### 1. **Categorical Feature Distribution**
![image](https://github.com/Shemnderitu/SyriaTel-Customer-Churn-Project/blob/master/images/image%206.png)

First piechart shows international plan distribution, Second piechart shows voice mail plan distribution, Third piechart shows churn distribution.

**Insights:**

- Most customers do not subscribe to the international or voicemail plan.

- Churned customers represent a small minority, confirming a class imbalance issue.

### 2. **Churn Distribution by Plan Subscription**
![image](https://github.com/Shemnderitu/SyriaTel-Customer-Churn-Project/blob/master/images/image%202.png)

**Insights:**

- Churn is more prevalent among users with the international plan, potentially due to cost sensitivity.

- Customers with a voice mail plan exhibit a lower churn rate, possibly indicating higher engagement.
  
### 3. **Correlation Heatmap & Redundancy Reduction**
![image](https://github.com/Shemnderitu/SyriaTel-Customer-Churn-Project/blob/master/images/image%205.png)

**Insights:**

- Total minutes and charges are almost perfectly correlated → keeping only one avoids redundancy.

- Customer service calls, international plan, and total day minutes have stronger relationships with churn.

---

## ⚙️ Modeling Approach

Three models were built and compared:

1. **Logistic Regression**:
   - Interpretable and lightweight.
   - Useful for quick baseline and high recall in identifying churners.

2. **Decision Tree**:
   - Provides clear decision rules.
   - Handles both categorical and continuous features with intuitive logic.

3. **Random Forest**:
   - Most robust and accurate.
   - Combines multiple trees and uses feature randomness to reduce overfitting.

### 🧪 Data Preparation Steps

- **SMOTE Oversampling** was used to balance the minority class (churners).
- **StandardScaler** was applied to numerical features for distance-based models.
- **Label Encoding** converted categorical values to numerical form.
- **Train-test split**: 80% training and 20% testing, with stratification to maintain class ratio.

---

## 📊 Model Evaluation

Each model was evaluated using:

- **Accuracy**: Overall prediction performance
- **Precision**: How many predicted churners were actually churners
- **Recall**: How many actual churners were correctly predicted
- **F1-score**: Balance between precision and recall
- **ROC-AUC**: Ability to distinguish between churn and non-churn

| Metric            | Logistic Regression | Decision Tree | Random Forest |
|------------------|---------------------|---------------|----------------|
| Accuracy          | 70%                 | 90%           | **90%**         |
| Precision (Churn) | 0.30                | 0.65          | **0.63**        |
| Recall (Churn)    | **0.76**            | 0.75          | 0.69            |
| ROC-AUC           | 0.7813              | 0.8423        | **0.8805**      |

- **Logistic Regression** captured most churners but with many false positives.
- **Decision Tree** had better balance and interpretability.
- **Random Forest** achieved the best overall performance and highest AUC score.

### 📊 ROC Curve Comparison
![image](https://github.com/Shemnderitu/SyriaTel-Customer-Churn-Project/blob/master/images/image%203.png)

- The closer the curve is to the top-left, the better. The Random Forest ROC curve dominates, confirming its superiority.

---

## 🔍 Feature Importance Analysis
![image](https://github.com/Shemnderitu/SyriaTel-Customer-Churn-Project/blob/master/images/image%204.png)

Using Random Forest, the following features emerged as key drivers of churn:
- Top predictors
1. **International plan**
2. **International minutes**
3. **Daytime minutes**

- Lower-ranked features with minimal influence
1. **Night calls**
2. **Voicemail services**

---

## ✅ Conclusion

- **Random Forest** is the most effective model due to its superior accuracy and discrimination ability.
- **Logistic Regression** is still valuable for early flagging of churners, especially when computational simplicity is needed.
- **Decision Tree** bridges interpretability and solid performance.

Together, the models provide actionable insights into who is likely to churn and why.

---

## 📌 Business Recommendations

- **Customer Service Optimization**: Prioritize support for users with frequent service calls.
- **Plan Review**: Evaluate international plan costs and usability—frequent usage here links to high churn.
- **Usage Monitoring**: Watch customers with high daytime and international call volumes.
- **Engagement Strategy**: Promote voicemail plans among at-risk customers to build service stickiness.

---

## 🚀 Next Steps

- Deploy Random Forest model in SyriaTel’s CRM for real-time churn detection.
- Build dashboards for churn alerts and team visibility.
- Retrain model every quarter with updated data.
- Consider new data sources such as billing complaints or mobile data consumption.

---

