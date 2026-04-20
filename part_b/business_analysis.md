# B1. Problem Formulation

## (a) Machine Learning Problem Formulation

This business problem can be formulated as a **supervised machine learning regression problem**.

* **Target Variable:**
  `items_sold` — the number of items sold in a store during a specific promotion period.

* **Input Features:**

  * Store attributes: `store_size`, `location_type`, `competition_density`
  * Promotion-related features: `promotion_type`
  * Temporal features: `month`, `day_of_week`, `is_weekend`, `is_festival`
  * Other behavioral indicators (if available): `footfall`, past sales trends

* **Type of Problem:**
  This is a **regression problem** because the target variable is continuous and numerical.

* **Justification:**
  The goal is to estimate the number of items sold under different promotional and store conditions. Since the output is a numeric value rather than a category, regression models are the most appropriate choice.

---

## (b) Why Items Sold is Better than Revenue

Using **items_sold (sales volume)** as the target variable is more reliable than using total revenue for the following reasons:

* Revenue can be heavily influenced by **price changes, discounts, and promotion strategies**, which may distort the actual effectiveness of a promotion.

* Items sold directly reflects **customer demand and response**, making it a more consistent and unbiased measure.

* Some promotions (such as heavy discounts) may increase the number of items sold but reduce revenue per item, leading to misleading conclusions if revenue is used as the target.

* **Broader Principle:**
  This highlights an important principle in machine learning:
  **The target variable must align closely with the actual business objective.**
  Choosing the wrong target can lead to incorrect insights and poor business decisions, even if the model performs well technically.

---

## (c) Alternative Modelling Strategy

Instead of using a single global model across all 50 stores, a more effective approach is to use a **segmented or hierarchical modelling strategy**.

* **Proposed Approach:**

  * Segment stores based on `location_type` (urban, semi-urban, rural) and/or other characteristics
  * Train separate models for each segment
    **OR**
  * Use clustering techniques to group similar stores and build models for each cluster

* **Justification:**

  * Customer behavior, purchasing power, and competition vary significantly across locations
  * The same promotion may perform differently in different store types
  * A single global model may fail to capture these variations and reduce prediction accuracy

* **Benefits:**

  * Improved model performance
  * More personalized promotion strategies
  * Better business decision-making at the store level

---

### Conclusion

By framing this as a regression problem, selecting the correct target variable, and adopting a segmented modelling approach, the retailer can significantly improve the effectiveness of its promotional strategies and maximize overall sales performance.

