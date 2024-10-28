# Customer LifeTime Value Forecasting Model

[![Customer Lifetime Value](https://business.trustedshops.com/hs-fs/hubfs/1-TS_B2B/content/uk/20230228-customer-lifetime-value/customer-life-value-formula.png?width=720&height=500&name=customer-life-value-formula.png)](https://en.wikipedia.org/wiki/Customer_lifetime_value)
<hr>

# Project Overview

> **Note:** Only a portion of the information and code is disclosed here for reference.

This project forecasts the **first and second repurchase rates** for three distinct brands: the established **Brand W** and the newer **Brands O and H**. Using these forecasted repurchase rates, we calculate the **predicted Customer Lifetime Value (LTV)** for each customer cohort. 

Our approach begins by segmenting customers by their initial purchase month, creating **monthly cohorts**. We set a retention period limit of **720 days (approximately 2 years)**, after which customers without a repurchase are considered to have churned. Additionally, we define two distinct order types: **One-Time Order** and **Subscription Order**. These allow us to analyze **four different order dynamics** across each brand:

- **One-Time to One-Time (OO)**
- **One-Time to Subscription (OS)**
- **Subscription to Subscription (SS)** – *largest proportion of repurchases*
- **Subscription to One-Time (SO)**

The project focuses on forecasting the repurchase rates across these four order dynamics for each brand. Cohorts with a first purchase date beyond the 720-day threshold were used as the training set. Using a **curve-fitting technique**, we gradually aligned cohorts with fewer than 720 days of data to match the trend observed in the training data.

### Brands

- **W** (Established brand)
- **O** (Newer brand)
- **H** (Newest brand)

### Order Types

- **One-Time Order**
- **Subscription Order**

### Order Dynamics

- **One-Time ➔ One-Time (OO)**
- **One-Time ➔ Subscription (OS)**
- **Subscription ➔ Subscription (SS)**: Largest proportion of repurchases
- **Subscription ➔ One-Time (SO)**

---

## Project Enhancements and Specific Revisions

### Challenge
While the repurchase rate prediction for **Brand W** was stable due to sufficient historical data, **Brands O and H**—with fewer observations beyond the 720-day retention threshold—exhibited overfitting issues. This resulted in anomalies, such as excessively steep slopes in the prediction graphs.

### Solution
To address these issues and improve accuracy:
1. **Data Augmentation for Training**: We selectively increased the training data size for Brands O and H by including randomly selected cohorts from the first repurchase data of Brand W, which had the highest data volume.
2. **Interval-Based Prediction Adjustment**: Recognizing that repurchases decreased rapidly after 200-240 days, we divided the 720-day period into two intervals. The anticipated values were calculated for the first interval, and the prediction trajectory for the second interval was adjusted to follow the trend at the end of the first interval.

Through this approach, we refined the curve-fitting model to provide a more accurate prediction for Brands O and H, while preserving the reliability of Brand W's predictions.

---

## Results

With these revisions, our model achieved an **LTV prediction accuracy of up to 92%** based on anticipated repurchase rates. This high-accuracy forecast was presented to C-level executives, providing valuable insights for future strategic decision-making.

