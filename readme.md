# 🏠 Predictive Analytics: KNN & XGBoost Regression

**Author:** Fatwa Nurhidayat  
**Focus:** Data Cleaning, Feature Engineering, Regression Modeling, and Predictive Insights.

---

## 📊 Project Overview

**Background** The real estate market is a cornerstone of the global economy. House prices are influenced by a complex interplay of physical attributes (bedrooms, bathrooms, living area), location, and temporal factors (year built/renovated). For buyers and investors, price uncertainty is a major hurdle.

Inspired by the work of **Yahya et al. (2021)**, this project applies Machine Learning to reduce market uncertainty. While the original study focused on Penang, Malaysia, this project adapts the methodology for the dynamic US housing market, providing a data-driven approach to property valuation.

**Strategic Impact & Business Value**
- **Informed Budgeting:** Helps home buyers assess if a property is fairly priced relative to its features.
- **Investment Optimization:** Assists investors in identifying high-potential properties and locations.
- **Urban Planning:** Provides insights for local governments to identify regional development needs.

---

## 🎯 Business Understanding

**Problem Statements**
1. **Price Disparity:** Buyers often struggle to estimate the fair market value of a property based solely on its physical characteristics.
2. **Model Selection:** Identifying the most effective regression model to capture the complex, non-linear relationships between property features and final sales prices.

**Goals**
1. **Accurate Estimation:** Develop a system to help stakeholders make informed purchasing or investment decisions.
2. **Model Optimization:** Evaluate and identify the most robust regression algorithm for high-precision price forecasting.

**Solution Approach**
- Comprehensive **Exploratory Data Analysis (EDA)** to uncover correlations and patterns.
- Implementation of **K-Nearest Neighbors (KNN)** and **XGBoost Regression**.
- Performance evaluation using the **R-squared (R²)** metric.

---

## 🔍 Data Understanding

**Dataset Description** The dataset contains 4,140 records of US housing transactions with 18 distinct features.
- **Source:** [Kaggle - USA House Prices](https://www.kaggle.com/datasets/fratzcan/usa-house-prices)

### Key Features
| Feature | Description |
|---|---|
| `Price` | Target Variable (USD). |
| `Sqft Living` | Living area in square feet. |
| `Bedrooms/Bathrooms` | Total count of rooms. |
| `Condition/View` | Quality indices (1-5 or 0-4). |
| `Waterfront` | Binary indicator for waterfront properties. |

---

## 🛠 Data Preparation

To ensure high model reliability, the following pipeline was implemented:
- **Outlier Management:** - Removed illogical records (e.g., houses with 0 bedrooms, 0 bathrooms, or 0 USD price).
    - Handled extreme values in `price` using **Log Transformation** to normalize the distribution.
    - Applied **Winsorization** to area features (`sqft_living`, `sqft_above`, etc.) to limit the influence of extreme outliers without losing data points.
- **Feature Selection:** Dropped irrelevant columns (`date`, `street`, `city`, `statezip`, `country`) and low-correlation features (`sqft_lot`, `condition`, `yr_built`, `yr_renovated`) to reduce noise.
- **Data Scaling:** Applied `StandardScaler` to ensure features are on a comparable scale for distance-based algorithms.
- **Data Splitting:** 80/20 Train-Test split.

---

## 🤖 Modeling

### 1. KNN Regression
- **Mechanism:** Predicts values based on the average of the *k* nearest data points.
- **Configuration:** `n_neighbors=8`.
- **Pros:** Excellent for non-linear relationships; simple to implement.

### 2. XGBoost Regression
- **Mechanism:** An advanced gradient boosting ensemble method.
- **Optimization:** Hyperparameter tuning via `GridSearchCV` (5-fold cross-validation).
- **Best Parameters:** `learning_rate: 0.1`, `max_depth: 3`, `n_estimators: 100`, `subsample: 0.8`.
- **Pros:** Robust against overfitting due to built-in regularization; highly efficient.

---

## 📈 Evaluation & Results

The models were evaluated using **R-squared (R²)**, which measures how well the model explains the variance in house prices.

| Model | R² Score |
|---|---|
| KNN | 0.83 |
| **XGBoost** | **0.91** |

**Conclusion:** The **XGBoost Regression** model outperformed KNN with an R² of **0.91**, indicating it can accurately explain 91% of the price variance. This high level of accuracy makes it a reliable tool for stakeholders to estimate property values based on specific physical and locational attributes.

---
*Developed by Fatwa Nurhidayat as part of a Machine Learning portfolio project.*