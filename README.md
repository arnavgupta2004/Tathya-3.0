# 📊 Zenkart Customer & Sales Analytics

### Data Science Case Study – Tathya 3.0 (Goa Institute of Management)

This project presents an **end-to-end data analytics and machine learning solution** for Zenkart, a rapidly growing Indian D2C tech accessories brand. The objective was to diagnose the company's **sales volatility, churn increase, and uneven product performance**, and provide **data-driven business strategies** to improve growth and customer retention.

This work was developed as part of **Tathya 3.0 – Data Science Competition conducted by Cognition (Data Science & Analytics Club), Goa Institute of Management**, where this project finished as a **Top 3 Finalist**.

---

# 🚀 Problem Statement

Zenkart experienced strong growth during **2023–2024**, but began facing issues in **early 2025**:

* Sales fluctuating unpredictably
* Declining repeat purchases
* Uneven SKU performance
* Delivery delays
* Customer behavior differences across cities
* Rising churn rates
* Unclear marketing effectiveness

The objective was to analyze transactional, customer, and product data to identify the root causes and propose **actionable strategies for growth and retention**.

---

# 📂 Dataset Overview

| Metric       | Value                          |
| ------------ | ------------------------------ |
| Transactions | **951**                        |
| Features     | **25 columns**                 |
| Data Types   | Numeric, Categorical, Temporal |

### Feature Categories

**Customer Demographics**

* Age
* CityTier
* Income

**Purchase Behaviour**

* Quantity
* TotalOrders
* NetSales

**Product Attributes**

* Category
* MRP
* Cost

**Service Quality**

* DeliveryTime
* Returned
* Rating

**Temporal Features**

* Year
* Month
* Week
* Day
* Time

---

# ⚙️ Data Preprocessing

### Date Decomposition

The `OrderDate` column was decomposed into:

* Year
* Month
* Week
* Day
* DayOfWeek
* Time

This enables:

* Seasonality detection
* Weekly trend analysis
* Forecast modeling

The original `OrderDate` column was removed to avoid redundancy.

---

# 🧹 Missing Value Treatment

| Feature      | Missing | Strategy                     | Reason                                  |
| ------------ | ------- | ---------------------------- | --------------------------------------- |
| DeliveryTime | 3.99%   | Median (Category × CityTier) | Delivery varies by location and product |
| Age          | 4.52%   | Median (CityTier)            | Demographics vary geographically        |
| Income       | 5.05%   | Median (CityTier)            | Income strongly linked to city tier     |
| Rating       | 22.08%  | Mode (Category)              | Product-specific feedback patterns      |

Conditional imputation was used instead of global averages to **preserve realistic behavioral patterns**.

---

# 📉 Outlier Detection

Outliers were detected using the **Interquartile Range (IQR) method**.

Affected variables:

* Price
* CLV
* DeliveryTime

Outliers were **capped using clipping** instead of deletion to maintain dataset integrity.

---

# 🧮 Feature Engineering

### NetSales

```
NetSales = Price × Quantity × (1 - Discount%)
```

This metric captures **true revenue after discounts** and was used throughout segmentation, churn modeling, and forecasting.

---

# 👥 Customer Segmentation

Customers were segmented using **K-Means clustering**.

### Features Used

* Age
* Income
* TotalOrders
* CLV
* TotalRevenue
* TotalQuantity
* AvgDeliveryTime
* Rating

### Optimal Clusters

* Silhouette Score → suggested **K = 2**
* Elbow Method → suggested **K = 3**

We selected **K = 3** for **better business interpretability**.

---

### Cluster Profiles

| Cluster   | Description                       | Strategy                             |
| --------- | --------------------------------- | ------------------------------------ |
| Cluster 0 | Mature high-value loyal customers | VIP membership & premium cross-sells |
| Cluster 1 | High spend power users            | Bundles & accessory upsell           |
| Cluster 2 | Young price-sensitive customers   | Cashback offers & faster delivery    |

---

# 🤖 Churn Prediction

Models built:

* Logistic Regression
* Random Forest
* XGBoost

### Model Performance

| Model               | Accuracy | AUC       |
| ------------------- | -------- | --------- |
| Logistic Regression | 85%      | 0.90      |
| Random Forest       | **97%**  | **0.986** |
| XGBoost             | 97%      | 0.983     |

Random Forest was chosen for final interpretation due to **high performance and strong feature importance insights**.

### Top Churn Drivers

1. TotalOrders
2. Income
3. CityTier
4. CLV
5. DeliveryTime

Key insight:
Customers churn primarily due to **low order frequency before habit formation**.

---

# 📊 Profitability Analysis

| Category         | NetSales | Profit | Margin    |
| ---------------- | -------- | ------ | --------- |
| Smartwatch       | ₹4724    | ₹4139  | **63.9%** |
| Cable            | ₹4691    | ₹3472  | 49.0%     |
| Laptop Accessory | ₹4942    | ₹3403  | 36.5%     |
| Earphones        | ₹4759    | ₹3073  | **26.5%** |

### Insight

Smartwatches provide the **highest margin opportunity**, while earphones require strategic bundling.

---

# 🔁 Customer Retention Analysis

### Repeat Customer Rate

**81.49%**

However, cohort analysis revealed **strong early churn**.

### Cohort Retention Pattern

| Month After First Purchase | Retention |
| -------------------------- | --------- |
| Month 1                    | 23.8%     |
| Month 2                    | 17.8%     |
| Month 3                    | 16.6%     |

Key insight:

> Most customers churn within the **first 90 days**.

---

# 📈 Time Series Forecasting

Weekly sales were forecast using an **ARIMA(1,1,1)** model.

### Model Validation

Forecasts were compared using **clean vs raw data**.

| Dataset    | MAPE   |
| ---------- | ------ |
| Clean Data | 0.6258 |
| Dirty Data | 0.6160 |

The forecast predicts **sales stabilization around ₹90K–₹100K per week over the next 12 weeks**.

---

# 📊 Key Insights

* Tier-2 cities show the **highest loyalty**
* Smartwatches offer the **highest margins**
* Early churn occurs within **90 days**
* High delivery variance impacts retention
* Young customers are **price sensitive but convertible**

---

# 📈 Marketing Execution Roadmap

| Quarter | Focus              | Action                                          |
| ------- | ------------------ | ----------------------------------------------- |
| Q1      | Fix churn          | Early repeat incentives & delivery improvements |
| Q2      | Boost revenue      | Smartwatch push, bundles, influencer marketing  |
| Q3      | Expand reach       | Offline pop-ups & tech event sponsorship        |
| Q4      | Optimize marketing | Recommendation engine & CLV-based pricing       |

---

# 🛠 Tech Stack

**Languages**

* Python

**Libraries**

* Pandas
* NumPy
* Scikit-learn
* Statsmodels
* Seaborn
* Matplotlib

**Models**

* K-Means Clustering
* Logistic Regression
* Random Forest
* XGBoost
* ARIMA Time Series

---

# 🏆 Competition Result

This project was presented at:

**Tathya 3.0 – Data Science & Analytics Competition**
Cognition (Data Science Club)
Goa Institute of Management

🥈 **Top 3 Finalist**

---

# 📌 Future Improvements

* RFM-based customer segmentation
* Real-time recommendation systems
* Deep learning demand forecasting
* Customer lifetime journey automation

---

# 👨‍💻 Author

**Arnav Gupta**
B.Tech – Data Science & Artificial Intelligence
IIIT Dharwad
